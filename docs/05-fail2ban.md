# 05 - Fail2Ban

## Objective

Detect and temporarily block repeated failed SSH login attempts.

## What Fail2Ban Does

Fail2Ban watches logs for repeated authentication failures. When a source exceeds the configured threshold, Fail2Ban adds a temporary ban using the local firewall.

## Useful Commands

```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
sudo journalctl -u fail2ban --since "24 hours ago"
```

## SSH Jail Example

```ini
[sshd]
enabled = true
port = ssh
filter = sshd
logpath = %(sshd_log)s
maxretry = 3
findtime = 10m
bantime = 24h
```

## Evidence to Capture

Use sanitized screenshots or copied output showing:

- Fail2Ban service status
- SSH jail status
- Number of currently banned IPs
- Total banned IPs
- Example failed login entries with IPs redacted

## Security Relevance

Fail2Ban does not replace proper SSH hardening, but it helps reduce repeated brute-force noise and makes attacks more expensive for automated scanners.
