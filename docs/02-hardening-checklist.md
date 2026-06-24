# 02 - Hardening Checklist

## System Updates

```bash
sudo apt update
sudo apt upgrade -y
```

## User and Access Review

```bash
who
last
id
getent passwd
```

Review local accounts and remove or disable anything not required.

## SSH Hardening

Recommended settings:

```text
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication no
KbdInteractiveAuthentication no
```

Verify active SSH settings:

```bash
sudo sshd -T | grep -E 'permitrootlogin|passwordauthentication|pubkeyauthentication|kbdinteractiveauthentication'
```

## Firewall

Enable UFW and allow only required ports.

Common baseline:

```bash
sudo ufw status verbose
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

SSH should ideally be limited to trusted sources or Tailscale.

## Fail2Ban

```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
```

## CrowdSec

```bash
sudo cscli metrics
sudo cscli decisions list
```

## Logs

```bash
sudo journalctl -u ssh --since "24 hours ago"
sudo journalctl -u fail2ban --since "24 hours ago"
sudo grep "Failed password" /var/log/auth.log
sudo grep "Invalid user" /var/log/auth.log
```

## Reverse Proxy

Review Caddy configuration and confirm that only intended services are exposed publicly.

```bash
sudo caddy validate --config /etc/caddy/Caddyfile
sudo systemctl status caddy
```
