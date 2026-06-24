# 10 - Lessons Learned

## Key Takeaways

A public VPS is constantly exposed to automated scanning. SSH hardening and firewall rules are not optional extras; they are baseline controls.

The most useful controls in this project were:

- Reducing exposed services
- Using SSH keys
- Disabling direct root login
- Reviewing logs regularly
- Using Fail2Ban for repeated SSH failures
- Using CrowdSec for broader suspicious behavior
- Using Tailscale for private access
- Separating public services from private administrative access
- Documenting changes and evidence

## What I Would Improve Next

- Restrict SSH to Tailscale only
- Add centralized log collection
- Add automated security status checks
- Add alerting for repeated failed login spikes
- Document firewall rules more formally
- Add screenshots of sanitized service status outputs
- Build a simple incident report template for future log reviews

## Career Relevance

This project demonstrates practical security work built on network and infrastructure experience. It shows the ability to harden systems, review logs, identify suspicious behavior, document risk, and recommend technical improvements.
