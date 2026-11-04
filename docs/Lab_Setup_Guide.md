# Isolated Lab Setup Guide

## Purpose

Build a small, disposable virtual lab for authorized defensive service assessment. The example uses a scanner VM at `192.168.56.10` and an intentionally vulnerable target at `192.168.56.20` on `192.168.56.0/24`. These values are examples, not proof of the VMs' actual addresses.

## 1. Create an isolated virtual network

Prefer a **host-only** network in VirtualBox or a **host-only/custom private** network in VMware. Do not use a bridged adapter. A NAT network can permit outbound connections and is not the preferred choice for this isolated lab.

1. Create a dedicated virtual network for this lab, using a subnet that does not overlap with networks you need to access.
2. Disable routing, forwarding, and internet sharing for that network. Do not configure a default gateway for the lab VMs.
3. If using DHCP, reserve or record the scanner and target addresses. Otherwise, assign addresses in the same subnet, such as the examples above.
4. Attach each VM's lab adapter to that exact network. Disable any other VM network adapters for the duration of the exercise.
5. Take clean snapshots of both VMs so the lab can be restored.

Hypervisor menus vary by version; consult the vendor's current documentation for the exact UI steps.

## 2. Prepare the virtual machines

- Use a supported hypervisor and an intentionally vulnerable training image that you are authorized to run.
- Give the scanner VM resources appropriate to the image and tools in use; the project brief suggests at least 2 vCPUs, 4 GB RAM, and a 25 GB virtual disk for Kali.
- Keep the target VM disposable. Do not use a real system, production data, or an exposed public image as the target.
- Keep hypervisor management interfaces and shared folders outside the target's reach where possible.

## 3. Verify isolation before assessment

Before starting any assessment:

- Confirm both VMs have only the dedicated lab adapter enabled and that it is attached to the intended host-only network.
- Confirm each VM has the expected lab address and no default route to another network.
- Confirm the host-only network has no bridge, NAT, or forwarding path to the production LAN or internet.
- If any setting or route is unclear, stop and resolve it before sending assessment traffic.

Record the verified topology, addresses, hypervisor/network settings, and verification time in the report. Repeat these checks after changing VM or host networking.

## 4. Keep the exercise bounded

Document the exact target address and permitted activities before beginning. Use only non-destructive checks appropriate for the lab. Do not attempt exploitation, credential attacks, denial of service, or tests outside the written scope. Stop immediately if traffic reaches an unexpected host or network.

## 5. Preserve evidence and clean up

Store original assessment outputs under `scans/` and screenshots under `assets/screenshots/`. Record timestamps, tool versions, and the command or procedure used, but redact credentials, tokens, and unrelated personal data before sharing. Do not edit original evidence; make redacted copies when needed.

When finished, shut down the VMs or disconnect their lab adapters, preserve only evidence needed for the report, and restore snapshots before reusing the environment.
