# Germany Server - Mon May 11 15:45:14 UTC 2026

## Command: `printf '[Unit]\nDescription=Cloudflare Tunnel for mhrv\nAfter=network.target\n\n[Service]\nType=simple\nExecStart=/usr/local/bin/cloudflared tunnel --url http://localhost:8080\nRestart=always\nRestartSec=5\nStandardOutput=append:/var/log/cloudflared.log\nStandardError=append:/var/log/cloudflared.log\n\n[Install]\nWantedBy=multi-user.target\n' > /etc/systemd/system/cloudflared-tunnel.service && cat /etc/systemd/system/cloudflared-tunnel.service`
```
Warning: Permanently added '46.224.130.78' (ED25519) to the list of known hosts.
[Unit]
Description=Cloudflare Tunnel for mhrv
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/cloudflared tunnel --url http://localhost:8080
Restart=always
RestartSec=5
StandardOutput=append:/var/log/cloudflared.log
StandardError=append:/var/log/cloudflared.log

[Install]
WantedBy=multi-user.target
```

## Exit Code: 0
