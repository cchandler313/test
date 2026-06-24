# Commands Used

## System

```bash
sudo apt update
sudo apt upgrade -y
hostnamectl
uptime
```

## SSH

```bash
sudo systemctl status ssh
sudo sshd -T | grep -E 'permitrootlogin|passwordauthentication|pubkeyauthentication'
sudo journalctl -u ssh --since "24 hours ago"
```

## Firewall

```bash
sudo ufw status verbose
sudo ufw status numbered
sudo ss -tulpn
```

## Fail2Ban

```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
sudo journalctl -u fail2ban --since "24 hours ago"
```

## CrowdSec

```bash
sudo cscli metrics
sudo cscli decisions list
sudo systemctl status crowdsec
```

## Caddy

```bash
sudo caddy validate --config /etc/caddy/Caddyfile
sudo systemctl status caddy
sudo journalctl -u caddy --since "24 hours ago"
```

## Tailscale

```bash
tailscale status
tailscale ip -4
sudo systemctl status tailscaled
```

## Log Review

```bash
sudo grep "Failed password" /var/log/auth.log
sudo grep "Invalid user" /var/log/auth.log
sudo grep "Accepted" /var/log/auth.log
```
