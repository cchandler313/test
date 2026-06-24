# 07 - Caddy and Cloudflare

## Objective

Use Caddy and Cloudflare to publish only intended services while keeping TLS simple and manageable.

## Caddy Role

Caddy acts as the VPS reverse proxy and handles HTTPS automatically.

Common validation commands:

```bash
sudo caddy validate --config /etc/caddy/Caddyfile
sudo systemctl status caddy
sudo journalctl -u caddy --since "24 hours ago"
```

## Cloudflare Role

Cloudflare is used for DNS, proxying, and public edge protection in front of selected public subdomains.

## Security Considerations

- Only publish services that need to be public
- Use authentication for private dashboards
- Avoid exposing homelab services directly
- Review Caddy access logs
- Keep public and private routes clearly separated
- Avoid committing Caddyfiles with sensitive internal hostnames or auth hashes

## Log Review

Caddy access logs can help answer:

- What endpoints are being hit?
- Are there repeated suspicious requests?
- Are bots scanning common paths?
- Are protected dashboards being probed?
