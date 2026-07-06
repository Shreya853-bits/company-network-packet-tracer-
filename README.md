# Simulated Company Network - Packet Tracer Project

This project is a CCNA-style fake company network built for Cisco Packet Tracer. It includes segmented departments, inter-VLAN routing, OSPF, DHCP relay, DNS/web services, ACLs, NAT overload, switch port security, LACP EtherChannel, Rapid PVST, planned STP root placement, disabled DTP on trunks, and syslog/NTP monitoring hooks.

Packet Tracer `.pkt` files are created inside Packet Tracer itself, so this folder gives you the full engineering package needed to build the simulation: topology, IP plan, copy-paste IOS configs, server settings, and validation tests.

## Project Goal

Build a small company network with realistic network-engineering tasks:

- Separate HR, Engineering, Sales, Servers, Management, and Branch networks.
- Route between VLANs using router-on-a-stick.
- Use OSPF between the HQ and branch routers.
- Use DHCP relay so clients get addresses from a central server.
- Use ACLs to block selected department traffic.
- Use NAT overload so private networks can reach a simulated internet server.
- Lock down access switch ports with sticky MAC port security.
- Bundle uplinks with LACP EtherChannel.
- Make the switching design more deliberate with Rapid PVST and a planned root bridge.
- Send logs and time-sync requests to the internal server where Packet Tracer supports those services.
- Document the network like a real implementation package.

## Advanced Companion Module

This repository also includes an optional pfSense/VirtualBox segmented firewall lab for a more security-focused portfolio angle. That module covers WAN, DMZ, Internal, and Restricted zones with least-privilege firewall rules, validation steps, and a browser-based evidence dashboard.

Key companion files:

- `index.html` - pfSense lab dashboard
- `quick-start.md` - shortest pfSense build path
- `pfSense-gui-steps.md` - pfSense interface and firewall rule walkthrough
- `firewall-rules.csv` - firewall policy table
- `validation-plan.md` - pfSense test matrix
- `submission-checklist.md` - pfSense evidence checklist
- `resume-interview-notes.md` - security lab interview notes

## Topology Summary

Devices:

- 3 routers: `R1-HQ`, `R2-BRANCH`, `R3-ISP`
- 4 switches: `SW1-CORE`, `SW2-HR-ENG`, `SW3-SALES-SERVER`, `SW4-BRANCH`
- 12 client PCs split across HR, Engineering, Sales, Branch, and Management
- 1 internal server: `CORP-SRV1`
- 1 simulated internet server: `INET-WEB1`

Core VLANs:

| VLAN | Name | Subnet | Gateway |
| --- | --- | --- | --- |
| 10 | HR | 192.168.10.0/24 | 192.168.10.1 |
| 20 | ENGINEERING | 192.168.20.0/24 | 192.168.20.1 |
| 30 | SALES | 192.168.30.0/24 | 192.168.30.1 |
| 40 | SERVERS | 192.168.40.0/24 | 192.168.40.1 |
| 99 | MANAGEMENT | 192.168.99.0/24 | 192.168.99.1 |
| 50 | BRANCH-LAN | 192.168.50.0/24 | 192.168.50.1 |

## Files

- `docs/business-case.md` - fictional business scenario and requirements
- `docs/topology.md` - device inventory, cabling, and port map
- `docs/ip-addressing.md` - subnets, static IPs, and DHCP ranges
- `docs/security-policy.md` - traffic policy matrix and ACL mapping
- `docs/packet-tracer-build-guide.md` - step-by-step Packet Tracer build instructions
- `docs/commands-cheatsheet.md` - useful router, switch, and client commands
- `docs/demo-script.md` - walkthrough script for a video, class demo, or interview
- `docs/final-report-template.md` - report template to complete after testing
- `docs/phase-2-enhancements.md` - optional upgrades after the base lab works
- `docs/qa-readiness-report.md` - current readiness score and remaining validation steps
- `docs/github-publishing-guide.md` - steps for publishing the project to GitHub
- `configs/*.cfg` - ready-to-paste Cisco IOS router and switch configs
- `configs/server-settings.md` - Packet Tracer server GUI settings
- `tests/validation-checklist.md` - pings, traceroutes, ACL, NAT, DHCP, and port-security tests
- `tools/static-audit.ps1` - local static checker for project completeness
- `docs/portfolio-writeup.md` - README/resume text you can reuse after taking screenshots
- `docs/troubleshooting.md` - common failure symptoms and fixes
- `screenshots/` - place topology and test screenshots here
- `.github/workflows/static-audit.yml` - GitHub Actions workflow for repository checks
- `LICENSE`, `CONTRIBUTING.md`, `SECURITY.md`, `CHANGELOG.md` - GitHub-ready project files

## Build Order

1. Open Cisco Packet Tracer and place the devices listed in `docs/topology.md`.
2. Cable the topology exactly as shown in the cabling table.
3. Rename every device to match the project docs.
4. Paste each config from `configs/` into the matching device CLI.
5. Configure `CORP-SRV1` and `INET-WEB1` using `configs/server-settings.md`.
6. Set client PCs to DHCP.
7. Run the tests in `tests/validation-checklist.md`.
8. Save the Packet Tracer file as `company-network.pkt` in this folder.
9. Take screenshots and place them in `screenshots/`.

## QA Target

The project currently has a practical readiness estimate of 94%, with a static audit score of 100% for required files, advanced network features, the optional pfSense companion lab, and GitHub-ready repository files. Run the audit with:

```powershell
powershell -ExecutionPolicy Bypass -File "company-network-packet-tracer\tools\static-audit.ps1" -MinimumScore 90
```

See `docs/qa-readiness-report.md` for the scoring details and the remaining Packet Tracer GUI checks needed to confirm 100%.

## What To Show In A Portfolio

Use this as a portfolio project by showing:

- The topology screenshot.
- VLAN and IP addressing tables.
- Router configs showing OSPF, NAT, ACLs, and DHCP relay.
- Switch configs showing VLANs, trunks, and port security.
- STP output showing the intended root bridge.
- Test screenshots proving allowed traffic works and blocked traffic fails.
- A final report using `docs/final-report-template.md`.

## GitHub Publishing

This folder is ready to become its own GitHub repository. Use `docs/github-publishing-guide.md` for the publish steps, suggested repo description, and suggested topics.
