# Contributing

This is a Packet Tracer portfolio lab. Contributions should keep the project buildable for CCNA-level Packet Tracer users.

## Before Submitting Changes

Run the static audit:

```powershell
powershell -ExecutionPolicy Bypass -File ".\tools\static-audit.ps1" -MinimumScore 90
```

## Contribution Guidelines

- Keep configs compatible with common Cisco Packet Tracer devices.
- Document any topology change in `docs/topology.md`.
- Update `docs/ip-addressing.md` if any subnet, gateway, or static address changes.
- Update `tests/validation-checklist.md` when adding or changing a feature.
- Do not add real credentials, private IPs from an actual organization, or sensitive screenshots.
- Keep `.pkt` files versionable when they represent the final lab.

## Suggested Change Types

- Packet Tracer compatibility fixes
- Better validation tests
- Clearer diagrams or screenshots
- Optional advanced feature configs
- Documentation improvements

