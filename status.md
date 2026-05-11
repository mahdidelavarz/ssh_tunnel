# Germany Server - Mon May 11 14:25:15 UTC 2026

## Command: `cat /etc/os-release && echo --- && uname -m && echo --- && lsb_release -cs && echo --- && cat /etc/apt/sources.list.d/docker.list && echo --- && sudo apt update 2>&1 | tail -30`
```
Warning: Permanently added '46.224.130.78' (ED25519) to the list of known hosts.
PRETTY_NAME="Ubuntu 22.04.5 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.5 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
---
x86_64
---
jammy
---
---

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Hit:1 https://mirror.hetzner.com/ubuntu/packages jammy InRelease
Hit:2 https://mirror.hetzner.com/ubuntu/packages jammy-updates InRelease
Hit:3 https://mirror.hetzner.com/ubuntu/packages jammy-backports InRelease
Hit:4 https://mirror.hetzner.com/ubuntu/security jammy-security InRelease
Reading package lists...
Building dependency tree...
Reading state information...
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

## Exit Code: 0
