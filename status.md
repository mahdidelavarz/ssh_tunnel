# Germany Server - Thu May 14 12:16:43 UTC 2026

## Command: `cd /root && rm -f openvpn-install.sh && curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh && chmod +x openvpn-install.sh && sudo ./openvpn-install.sh uninstall --force 2>/dev/null; sudo ./openvpn-install.sh install --client vpnclient --no-client-password && echo ===START_CONFIG=== && cat /root/vpnclient.ovpn && echo ===END_CONFIG=== && echo SUCCESS`
```
Warning: Permanently added '78.47.70.169' (ED25519) to the list of known hosts.
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0100  144k  100  144k    0     0   786k      0 --:--:-- --:--:-- --:--:--  783k
[ERROR] Unknown option: --no-client-password. See 'openvpn-install install --help' for usage.
        Check the log file for details: openvpn-install.log
```

## Exit Code: 1
