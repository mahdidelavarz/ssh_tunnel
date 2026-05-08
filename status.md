# Germany Server - Fri May  8 16:52:03 UTC 2026

## Command: cat /root/gost.log
```
OpenSSH_9.6p1 Ubuntu-3ubuntu13.15, OpenSSL 3.0.13 30 Jan 2024
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug1: Connecting to 46.225.109.36 [46.225.109.36] port 22.
debug1: Connection established.
debug1: identity file /home/runner/.ssh/id_rsa type -1
debug1: identity file /home/runner/.ssh/id_rsa-cert type -1
debug1: identity file /home/runner/.ssh/id_ecdsa type -1
debug1: identity file /home/runner/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/runner/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/runner/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/runner/.ssh/id_ed25519 type -1
debug1: identity file /home/runner/.ssh/id_ed25519-cert type -1
debug1: identity file /home/runner/.ssh/id_ed25519_sk type -1
debug1: identity file /home/runner/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/runner/.ssh/id_xmss type -1
debug1: identity file /home/runner/.ssh/id_xmss-cert type -1
debug1: identity file /home/runner/.ssh/id_dsa type -1
debug1: identity file /home/runner/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_9.6p1 Ubuntu-3ubuntu13.15
debug1: Remote protocol version 2.0, remote software version OpenSSH_8.9p1 Ubuntu-3ubuntu0.13
debug1: compat_banner: match: OpenSSH_8.9p1 Ubuntu-3ubuntu0.13 pat OpenSSH* compat 0x04000000
debug1: Authenticating to 46.225.109.36:22 as 'root'
debug1: load_hostkeys: fopen /home/runner/.ssh/known_hosts: No such file or directory
debug1: load_hostkeys: fopen /home/runner/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: sntrup761x25519-sha512@openssh.com
debug1: kex: host key algorithm: ssh-ed25519
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-ed25519 SHA256:RUe4LqfxPiJ+UHzto5a9eGwNq9m0+INRcbuYM7BsmjQ
debug1: load_hostkeys: fopen /home/runner/.ssh/known_hosts: No such file or directory
debug1: load_hostkeys: fopen /home/runner/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: SELinux support disabled
Warning: Permanently added '46.225.109.36' (ED25519) to the list of known hosts.
debug1: check_host_key: hostkey not known or explicitly trusted: disabling UpdateHostkeys
debug1: ssh_packet_send2_wrapped: resetting send seqnr 3
debug1: rekey out after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: ssh_packet_read_poll2: resetting read seqnr 3
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey in after 134217728 blocks
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_ext_info_client_parse: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@openssh.com,webauthn-sk-ecdsa-sha2-nistp256@openssh.com>
debug1: kex_ext_info_check_ver: publickey-hostbound@openssh.com=<0>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Will attempt key: /home/runner/.ssh/id_rsa 
debug1: Will attempt key: /home/runner/.ssh/id_ecdsa 
debug1: Will attempt key: /home/runner/.ssh/id_ecdsa_sk 
debug1: Will attempt key: /home/runner/.ssh/id_ed25519 
debug1: Will attempt key: /home/runner/.ssh/id_ed25519_sk 
debug1: Will attempt key: /home/runner/.ssh/id_xmss 
debug1: Will attempt key: /home/runner/.ssh/id_dsa 
debug1: Trying private key: /home/runner/.ssh/id_rsa
debug1: Trying private key: /home/runner/.ssh/id_ecdsa
debug1: Trying private key: /home/runner/.ssh/id_ecdsa_sk
debug1: Trying private key: /home/runner/.ssh/id_ed25519
debug1: Trying private key: /home/runner/.ssh/id_ed25519_sk
debug1: Trying private key: /home/runner/.ssh/id_xmss
debug1: Trying private key: /home/runner/.ssh/id_dsa
debug1: Next authentication method: password
Authenticated to 46.225.109.36 ([46.225.109.36]:22) using "password".
debug1: channel 0: new session [client-session] (inactive timeout: 0)
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: pledge: network
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug1: Sending environment.
debug1: channel 0: setting env LANG = "C.UTF-8"
debug1: Sending command: cat /root/gost.log
debug1: pledge: fork
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
{"handler":"auto","kind":"service","level":"info","listener":"tcp","msg":"listening on [::]:443/tcp","service":"service-0","time":"2026-05-08T16:46:25.328Z"}
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 3224, received 3708 bytes, in 0.9 seconds
Bytes per second: sent 3570.0, received 4106.0
debug1: Exit status 0
```

## Exit Code: 0
