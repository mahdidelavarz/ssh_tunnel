# Germany Server - Mon May 11 14:53:50 UTC 2026

## Command: `docker ps --filter name=mhrv-tunnel && echo --- && docker logs mhrv-tunnel 2>&1 | tail -10`
```
Warning: Permanently added '46.224.130.78' (ED25519) to the list of known hosts.
CONTAINER ID   IMAGE                                          COMMAND         CREATED              STATUS              PORTS                                         NAMES
289d8c6b58d3   ghcr.io/therealaleph/mhrv-tunnel-node:latest   "tunnel-node"   About a minute ago   Up About a minute   0.0.0.0:8080->8080/tcp, [::]:8080->8080/tcp   mhrv-tunnel
---
[2m2026-05-11T14:52:38.006995Z[0m [32m INFO[0m [2mtunnel_node[0m[2m:[0m tunnel-node listening on 0.0.0.0:8080
```

## Exit Code: 0
