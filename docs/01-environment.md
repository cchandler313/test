# 01 - Environment

## Purpose

This VPS functions as a public-facing external Linux server used for reverse proxying, remote access, and security monitoring.

## Core Components

| Component | Description |
|---|---|
| Linux VPS | External public server |
| Caddy | Reverse proxy and automatic HTTPS |
| Cloudflare | DNS/proxying/protection for public subdomains |
| Tailscale | Private mesh access |
| UFW | Local host firewall |
| Fail2Ban | SSH brute-force protection |
| CrowdSec | Behavioral detection and firewall blocking |
| systemd | Service management |
| journalctl/auth logs | Log review sources |

## Security Concerns

Because the VPS is internet-facing, the main security concerns are:

- SSH brute-force attempts
- Public service exposure
- Misconfigured reverse proxy rules
- Weak authentication
- Unpatched packages
- Poor logging or lack of visibility
- Accidental exposure of private homelab services

## Security Objective

The objective was to reduce attack surface, improve visibility, and make administrative access more controlled.
