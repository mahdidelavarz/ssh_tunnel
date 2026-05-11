# Germany Server - Mon May 11 15:46:43 UTC 2026

## Command: `systemctl daemon-reload && systemctl enable cloudflared-tunnel && systemctl start cloudflared-tunnel && sleep 5 && systemctl status cloudflared-tunnel --no-pager 2>&1 | head -15`
```
Warning: Permanently added '46.224.130.78' (ED25519) to the list of known hosts.
Created symlink /etc/systemd/system/multi-user.target.wants/cloudflared-tunnel.service → /etc/systemd/system/cloudflared-tunnel.service.
● cloudflared-tunnel.service - Cloudflare Tunnel for mhrv
     Loaded: loaded (/etc/systemd/system/cloudflared-tunnel.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2026-05-11 15:46:46 UTC; 5s ago
   Main PID: 14314 (cloudflared)
      Tasks: 5 (limit: 4530)
     Memory: 13.9M
        CPU: 288ms
     CGroup: /system.slice/cloudflared-tunnel.service
             └─14314 /usr/local/bin/cloudflared tunnel --url http://localhost:8080

May 11 15:46:46 88ljfjcpl4 systemd[1]: Started Cloudflare Tunnel for mhrv.
```

## Exit Code: 0
