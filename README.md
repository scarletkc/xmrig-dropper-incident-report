# Incident Report: Unauthorized XMRig Miner Dropper on Azure VM

> **⚠️ DO NOT RUN ANY SCRIPTS OR BINARIES IN THIS REPOSITORY.**
>
>  With mandatory safety disclaimer and usage restrictions

## Context (What happened)

A previously compromised Ubuntu server (Azure VM) was found running an unauthorized cryptocurrency miner.
During incident response and offline disk inspection, I located a shell script dropper (`sex.sh`) that:
- downloads XMRig from the official GitHub release page,
- sets mining parameters (pool + wallet),
- attempts persistence via `systemd` (service name: `system-update-service`),
- falls back to `nohup` if `systemd` setup fails.

This repository is **for documentation, threat intelligence sharing (IOCs), and defensive learning only**.

## Why I’m publishing this

- To help others recognize the same patterns quickly
- To preserve indicators of compromise (IOCs) for defenders
- To document the incident timeline and remediation steps

I am **not** distributing malware. Any content here must **not** be executed.

## Key Indicators (IOCs)

- **Dropper script path observed**: `/nextjsproject/sex.sh`
- **Archive name used**: `kal.tar.gz`
- **Extracted directory**: `xmrig-6.24.0/`
- **Persistence**: `systemd` service named `system-update-service`
- **Miner**: `xmrig` (Monero / XMR CPU miner)

> Note: Some values may be partially redacted to prevent abuse.

## Reference: XMRig download source

The dropper downloads XMRig from the official release URL:
- https://github.com/xmrig/xmrig/releases

## Files in this repository

- **[DO NOT RUN THIS SHELL.txt](./DO%20NOT%20RUN%20THIS%20SHELL.txt)**
- `sex.sh` — malicious dropper script (text evidence only; **do not run**)

## Responsible use

If you are not a security professional with an isolated lab environment, **do not download or handle any suspicious binaries**.
For regular users: treat this repository as a **read-only warning and reference**.

## License

This repository is shared for educational and defensive purposes. No warranty. Use at your own risk.
