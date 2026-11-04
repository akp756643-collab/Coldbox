

A defensive assessment project for an intentionally vulnerable target in an isolated virtual lab. The repository provides lab setup guidance, an evidence-handling structure, and a report template; it does not contain scan results.

## Scope and safety

- Assess only the target VM you own or have explicit permission to assess.
- Keep the scanner and target on a host-only virtual network with no bridged adapter or route to a production LAN or the internet.
- The example addresses below are documentation values. Confirm the lab's actual addresses before any assessment.
- Use non-destructive checks, follow the hypervisor and scanner documentation, and stop if traffic leaves the lab.
- Do not treat the example services or findings in the project brief as verified results. Record a finding only when supported by collected evidence.
- This repository does not provide exploitation steps or automated vulnerability testing.

## Lab topology

| System | Example address | Role |
| --- | --- | --- |
| Kali Linux VM | `192.168.56.10` | Authorized assessment workstation |
| Intentionally vulnerable Linux VM | `192.168.56.20` | Lab target |
| Virtual network | `192.168.56.0/24` | Host-only; isolated from other networks |

See [the lab setup guide](docs/Lab_Setup_Guide.md) before connecting either VM.

## Repository layout

```text
docs/
  Lab_Setup_Guide.md
  Vulnerability_Report.md
scans/
  README.md
assets/
  screenshots/
    README.md
.gitignore
```

Add scan exports and screenshots only after collecting them in the authorized lab. The report is a Markdown source template; it should be completed and reviewed before producing a final report.

## Assessment workflow

1. Configure and verify the isolated lab.
2. Record the assessment date, exact target, authorization, and permitted test scope.
3. Perform only approved, non-destructive service identification inside the lab.
4. Preserve original outputs and screenshots; redact credentials and other sensitive data before sharing.
5. Validate each suspected issue against authoritative vendor or vulnerability references, document evidence and limitations, and prioritize remediation.
6. Re-test remediation within the same authorized scope and update the report.

## Current status

No scans, screenshots, or independently verified findings were supplied with the project brief. The report therefore starts with unverified hypotheses and empty evidence fields.
