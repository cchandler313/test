# 04 - Firewall and UFW

## Objective

Limit public exposure to only required services.

## Baseline Rules

The VPS should deny unsolicited inbound traffic by default and only allow required services.

Example:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status verbose
```

## SSH Access

If SSH is required publicly:

```bash
sudo ufw allow 22/tcp
```

Preferred future state:

```bash
sudo ufw allow in on tailscale0 to any port 22 proto tcp
sudo ufw deny 22/tcp
```

This allows SSH over Tailscale while blocking public SSH.

## Validation

```bash
sudo ufw status numbered
sudo ss -tulpn
```

## Security Relevance

Firewall rules reduce the attack surface by limiting what external systems can reach. Even when services are hardened, unnecessary exposure creates unnecessary risk.
