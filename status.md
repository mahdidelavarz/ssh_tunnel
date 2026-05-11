# Germany Server - Mon May 11 14:36:40 UTC 2026

## Command: `nohup cloudflared tunnel --url http://localhost:8080 > /root/cloudflared.log 2>&1 & sleep 5 && cat /root/cloudflared.log | grep -oP 'https://[a-z0-9-]+\.trycloudflare\.com' | tail -1`
```
Warning: Permanently added '46.224.130.78' (ED25519) to the list of known hosts.
```

## Exit Code: 0
