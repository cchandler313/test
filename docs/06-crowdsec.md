# 06 - CrowdSec

## Objective

Add behavioral detection and firewall enforcement for suspicious activity.

## What CrowdSec Adds

CrowdSec analyzes logs and applies decisions based on known suspicious behaviors. With a firewall bouncer, those decisions can be enforced at the host level.

## Useful Commands

```bash
sudo cscli metrics
sudo cscli decisions list
sudo systemctl status crowdsec
```

## Evidence to Capture

Use sanitized output showing:

- CrowdSec service running
- Parsed log sources
- Local API metrics
- Active decisions
- Firewall bouncer status, if installed

## Security Relevance

CrowdSec adds another layer of detection beyond simple repeated SSH failure matching. It can identify broader patterns of abusive behavior and enforce blocking decisions.
