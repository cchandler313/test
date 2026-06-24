# 03 - SSH Hardening

## Objective

Reduce the risk of unauthorized access through SSH.

## Risks

Public SSH services are frequently targeted by automated scanners and brute-force attempts. Common usernames such as `admin`, `root`, `guest`, `test`, and `ubuntu` are often attempted repeatedly.

## Controls Applied

| Control | Purpose |
|---|---|
| Disable root login | Prevent direct root authentication |
| Prefer SSH keys | Reduce password-guessing risk |
| Disable password login after key validation | Prevent brute-force password attempts |
| Use Fail2Ban | Temporarily ban repeated failed login sources |
| Use CrowdSec | Add behavioral detection and bouncer enforcement |
| Limit SSH exposure | Prefer access through Tailscale or trusted IPs |

## Verification Commands

```bash
sudo sshd -T | grep permitrootlogin
sudo sshd -T | grep passwordauthentication
sudo sshd -T | grep pubkeyauthentication
sudo systemctl status ssh
```

## Recommended Configuration

```text
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication no
KbdInteractiveAuthentication no
```

## Notes

Before disabling password authentication, confirm that SSH key login works from a second active session. Locking yourself out of a VPS is a tiny paperwork dragon with teeth.
