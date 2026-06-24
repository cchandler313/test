# 09 - Log Review Case Study

## Case 001: Repeated SSH Login Failures

### Summary

The VPS authentication logs showed repeated failed SSH login attempts from external sources. The attempted usernames included common defaults and invalid users.

### Example Sanitized Evidence

```text
Jun 16 11:37:52 vps sshd[12345]: Invalid user admin from <PUBLIC_IP_REDACTED> port 34894
Jun 16 11:37:54 vps sshd[12345]: Failed password for invalid user admin from <PUBLIC_IP_REDACTED> port 34894 ssh2
Jun 16 11:39:52 vps sshd[12345]: Timeout before authentication for connection from <PUBLIC_IP_REDACTED>
```

### Analysis

This activity is consistent with automated SSH brute-force scanning. Public VPS hosts commonly receive this type of traffic shortly after being exposed to the internet.

### Response

- Reviewed SSH authentication logs
- Confirmed invalid usernames were being attempted
- Checked Fail2Ban SSH jail status
- Reviewed CrowdSec activity
- Verified firewall posture
- Recommended disabling password authentication after confirming SSH keys
- Recommended limiting SSH to Tailscale where possible

### Risk Rating

**Medium**

The attempts themselves are common internet noise, but public SSH with password authentication enabled would increase risk.

### Recommendation

Use SSH keys, disable root login, disable password authentication, keep Fail2Ban and CrowdSec active, and restrict SSH to Tailscale or trusted sources if possible.
