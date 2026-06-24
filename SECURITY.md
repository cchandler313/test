# Security and Sanitization Notes

This repository is intended for portfolio documentation only.

Before publishing screenshots, logs, or configuration files, sanitize:

- Public IP addresses
- Private IP addresses
- Usernames
- Email addresses
- API keys
- Tokens
- Hostnames that should not be public
- Cloudflare account details
- Tailscale device names or tailnet details
- Basic auth hashes
- Caddyfile entries that reveal private services
- Any internal service URLs

Use placeholders such as:

```text
<PUBLIC_IP_REDACTED>
<PRIVATE_IP_REDACTED>
<USERNAME_REDACTED>
<DOMAIN_REDACTED>
<TAILSCALE_IP_REDACTED>
```

Do not commit secrets to GitHub. If a secret is accidentally committed, rotate it immediately and remove it from Git history.
