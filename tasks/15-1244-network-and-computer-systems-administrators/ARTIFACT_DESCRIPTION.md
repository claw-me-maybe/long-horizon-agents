# Terraform Module + Runbook: Multi-AZ PostgreSQL RDS for Lumeria Insurance Claims API

## Occupation
- **SOC:** 15-1244
- **Title:** Network and Computer Systems Administrators

## Scenario
Lumeria Insurance, a mid-size commercial P&C carrier, is migrating its claims API backend from a self-managed Postgres 13 on EC2 to AWS RDS Postgres 16 to reduce on-call burden. SysAdmin lead Yusef Abdellah needs to deliver a reusable Terraform module + runbook by May 8, 2026 so that staging, UAT, and prod environments can be stood up consistently, and so the junior on-call can execute failover drills without paging Yusef at 2 AM. The previous manual deployment in March leaked a read replica endpoint to a public security group for 40 minutes.

## Inputs
- **Accounts:** `lumeria-staging` (123456789012), `lumeria-uat` (234567890123), `lumeria-prod` (345678901234).
- **Region:** `us-east-2` primary, `us-west-2` disaster recovery.
- **VPC:** existing, with private subnets tagged `Tier=data` in 3 AZs per region. VPC IDs in SSM `/lumeria/<env>/vpc_id`.
- **Instance sizing target:** prod = `db.m6g.2xlarge` Multi-AZ, replicas = 2 in same region + 1 cross-region read-replica. UAT/staging = `db.m6g.large` single-AZ, no replicas.
- **Storage:** gp3, 500 GB prod / 100 GB lower envs, encrypted with a per-env KMS CMK (existing, ARNs in SSM).
- **Backups:** 30 days retention prod, 7 days lower envs, PITR on.
- **Parameter group tweaks:** `shared_buffers = {DBInstanceClassMemory/4}`, `log_min_duration_statement = 500`, `rds.force_ssl = 1`.
- **Monitoring:** Enhanced monitoring 15s, Performance Insights 7-day retention (or 2 years in prod), CloudWatch alarms for CPU >80% 5min, FreeStorageSpace <20%, ReplicaLag >60s.
- **Secrets:** master password rotated via Secrets Manager with 30-day rotation Lambda.
- **Compliance:** NAIC Model #668 requires claims data encrypted at rest + in transit; PII column access logged.

## Artifact specification
A **Terraform module + operational runbook** as two files inside the module dir. Required structure:

### File 1: `main.tf` (module)
Inputs via `variables.tf`, resources via `main.tf`, outputs via `outputs.tf`. At minimum:
- `aws_db_subnet_group` across 3 AZs.
- `aws_db_parameter_group` with the tuning above.
- `aws_security_group` that allows 5432 only from a list of source SGs (no CIDRs, no 0.0.0.0/0).
- `aws_db_instance` primary, conditional Multi-AZ.
- `aws_db_instance` read replicas (count-based).
- Optional cross-region replica behind a `var.enable_cross_region_replica` flag.
- `aws_secretsmanager_secret` + rotation schedule.
- CloudWatch alarms + SNS topic for paging.
- Tags block: `Environment`, `Owner=platform-eng`, `CostCenter=CC-4401`, `DataClass=pii-restricted`.

### File 2: `RUNBOOK.md`
Operational runbook with H2 sections:
1. **Purpose & scope**
2. **Pre-change checklist** (approval, maintenance window, backup taken)
3. **Standard operating procedures:**
   - Deploy/update: `terraform plan/apply` with required review gates
   - Failover drill (Multi-AZ)
   - Promote cross-region replica (DR drill)
   - Rotate master password
   - Restore to point-in-time
4. **Incident response** — top 5 alarms with first-responder steps
5. **Rollback procedure**
6. **Post-change verification checklist**
7. **On-call escalation matrix** with names, phones, and schedule link.

## Output format
Two files in one `.md` (for this artifact), with Terraform in HCL fenced blocks and runbook as prose+checklists. ~360 lines total.

## Iteration targets
1. Replace hard-coded values with variables + sane defaults; add `validation {}` blocks (e.g. `instance_class` must match `db.m6g.*`).
2. Add `lifecycle { prevent_destroy = true }` on the prod DB resource + a `precondition` that blocks apply if `var.environment == "prod"` and `skip_final_snapshot == true`.
3. Harden the security group: deny egress by default except to Secrets Manager VPC endpoint and VPC CIDR.
4. Add a Terraform module README with a minimal usage example and input/output variable tables (auto-generated via `terraform-docs`).
5. Rewrite the failover-drill runbook section as a numbered, timestamped procedure with expected CloudWatch signals at each step.
6. Add a "least-privilege IAM for the rotation Lambda" resource and remove any `AdministratorAccess`-style role.

## Success criteria
- `terraform validate` and `terraform fmt -check` both pass.
- No publicly-routable resources; SG ingress list comes only from other SG IDs.
- Secrets Manager rotation is wired end-to-end (Lambda ARN, rotation schedule, DB user rotation).
- Every resource is tagged with at least `Environment`, `Owner`, and `CostCenter`.
- Runbook failover drill reads like a checklist a non-author could execute at 2 AM.
- Prod-specific safeguards (prevent_destroy, skip_final_snapshot=false, retention 30d) are conditional on env.

## Scope target
V1 at ~15 min: a single-AZ RDS instance resource, a basic SG restricted to one source SG, hard-coded instance class, one CloudWatch alarm, and a runbook skeleton with section headers + one filled-in SOP (deploy). Multi-AZ, replicas, cross-region, rotation Lambda, and full incident response content come in v2/v3.
