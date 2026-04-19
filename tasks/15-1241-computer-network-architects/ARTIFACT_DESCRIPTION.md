# Network Topology Design: Greenfield Dual-Datacenter with Azure ExpressRoute for Harrow-Vance Logistics

## Occupation
- **SOC:** 15-1241
- **Title:** Computer Network Architects

## Scenario
Harrow-Vance Logistics, a $1.2B freight brokerage, is consolidating 9 regional offices into two new datacenters (Dallas primary, Atlanta DR) and adopting Azure as the secondary compute tier. Chief Architect Solange Beaumont has tasked you with producing a network topology design package before the June 16, 2026 contract-signing gate with the DC colocation provider (QTS Dallas DFW-1). The design must support 4,200 WFH staff, a 95th-percentile cross-DC replication throughput of 8 Gbps for the IBM TM1 planning system, and 99.995% availability for the TMS application.

## Inputs
- **Scale:**
  - 4,200 WFH users (peak concurrent ~2,800), SSL VPN via Zscaler ZPA.
  - 9 offices being decommissioned over 12 months; 4 remain as small sales offices (10-30 users each).
  - ~900 VMs across the two DCs; ~300 Azure VMs in East US / Central US regions.
- **Traffic classes:**
  - TMS (dispatch): <50ms RTT required office→DC, jitter <5ms.
  - VoIP (Teams): DSCP EF, ~2,800 concurrent calls peak.
  - Bulk backup replication: Veeam, 8 Gbps sustained 2-8 AM CT.
  - IBM TM1 OLAP cubes: bursty, 200ms sensitive.
- **Security posture:**
  - Zero-trust network access (ZTNA) for WFH; east-west segmentation via Illumio.
  - PCI-DSS scope: payment processing VLAN isolated, attestation-of-compliance due annually.
  - SOC 2 Type II in progress.
- **Compliance/constraints:**
  - Dual-provider WAN required (Lumen + AT&T) — no single carrier.
  - ExpressRoute required (no public Azure IPs for prod workloads) at 10 Gbps bandwidth.
  - IPv4 exhaust: must use RFC1918 only, with summarizable blocks per site.
- **Budget target:** $4.8M capex, $1.6M/yr opex for WAN + DC interconnect.

## Artifact specification
A **network design document** with topology diagrams and specs. Required H2 sections:

1. **Executive summary** — business drivers, constraints, high-level design decision.
2. **Requirements & constraints** — functional, non-functional (SLAs, RPO/RTO), compliance.
3. **Logical topology** — mermaid or ASCII diagram showing: two DCs, Azure regions, ExpressRoute circuits, MPLS/SD-WAN, office sites, WFH path via ZPA.
4. **Physical topology** — rack-level for each DC: core (pair), distribution/spine, leaf, edge routers, firewalls. Include device models and interface counts.
5. **IP address plan** — RFC1918 allocation strategy. Show the /16 summary per site, /24 per VLAN, reserved blocks for growth, loopbacks, point-to-point /31s.
6. **Routing design** — IGP (OSPF area plan or IS-IS), BGP (iBGP full mesh or route-reflectors, eBGP to carriers, private ASNs for Azure peering).
7. **Segmentation & security zones** — zone model (DMZ, prod, dev, mgmt, PCI), firewall placement, east-west policy enforcement approach.
8. **Redundancy & failure scenarios** — HA design for core, edge, WAN, DC interconnect. Walk through 3 failure scenarios (single ER circuit down, entire DC down, carrier BGP flap) with expected RTO.
9. **QoS design** — DSCP markings per traffic class, per-hop behaviors, shaping/policing on WAN edges.
10. **Capacity plan** — bandwidth sizing per link with utilization headroom (target <60% steady state).
11. **Migration plan** — cutover waves from 9 offices to final-state topology.
12. **BOM summary** — device list with quantity, cost category, and budget roll-up.

## Output format
Single `.md` file, ~400 lines. Must include at least 3 diagrams (mermaid or structured ASCII): logical topology, physical rack layout for one DC, and an IP addressing tree.

## Iteration targets
1. Refine the IP plan to be strictly summarizable — each DC on a /15 that splits cleanly across aggregation routers; each office on a /20 with nibble-aligned VLAN /24s.
2. Add active-active ExpressRoute with local preference + AS-path prepending for DR steering; show failover time math.
3. Replace single-firewall DMZ with HA pair in active/standby with stateful sync link; specify the VIP / clustering method.
4. Add a detailed failure-scenario walkthrough for "Dallas DC full power loss during business hours" with traffic re-steering sequence and estimated user impact.
5. Add DSCP-to-queue mapping table on the WAN edge and specify WRED thresholds for bulk vs business-critical classes.
6. Harden the BGP design: add BFD (3x50ms), MD5 auth on eBGP, AS-path filtering toward carriers, and max-prefix limits.

## Success criteria
- All IP allocations are within RFC1918 and mathematically summarizable at site boundaries.
- Every SLA claim (availability, RPO/RTO) is tied to a specific design element (dual circuits, active-active, etc.), not just asserted.
- Device models and interface counts are explicit (e.g. Cisco Nexus 9336C-FX2, 36x100G).
- Routing design unambiguously states IGP areas and BGP ASNs, with loopback addressing.
- Failure scenarios have concrete RTO numbers justified by protocol timers (BFD, BGP, VRRP).
- BOM rolls up to a number that fits the $4.8M capex envelope (or explicitly flags where it doesn't).

## Scope target
V1 at ~15 min: exec summary, a single-panel logical topology diagram (DCs + Azure + offices), a flat IP plan (one block per DC), a sentence on OSPF and BGP, a note about "dual firewalls for HA," and a QoS class list without markings. Physical rack, failure-scenario walkthroughs, BGP timers/auth, and full BOM are v2/v3.
