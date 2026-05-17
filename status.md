# Germany Server - Sun May 17 04:35:21 UTC 2026

## Command: `cd /root && curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh && chmod +x openvpn-install.sh && sudo ./openvpn-install.sh install --client vpnclient --port 443 --protocol tcp && cat /root/vpnclient.ovpn`
```
Warning: Permanently added '49.12.68.126' (ED25519) to the list of known hosts.
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0100  144k  100  144k    0     0  1385k      0 --:--:-- --:--:-- --:--:-- 1393k
[INFO] === OpenVPN Non-Interactive Install ===
[INFO] Running in non-interactive mode with the following settings:
[INFO]   ENDPOINT=49.12.68.126
[INFO]   ENDPOINT_TYPE=4
[INFO]   CLIENT_IPV4=y
[INFO]   CLIENT_IPV6=n
[INFO]   VPN_SUBNET_IPV4=10.8.0.0
[INFO]   VPN_SUBNET_IPV6=fd42:42:42:42::
[INFO]   PORT=443
[INFO]   PROTOCOL=tcp
[INFO]   DNS=cloudflare
[INFO]   MULTI_CLIENT=n
[INFO]   AUTH_MODE=pki
[INFO]   CLIENT=vpnclient
[INFO]   CLIENT_CERT_DURATION_DAYS=3650
[INFO]   SERVER_CERT_DURATION_DAYS=3650
[INFO] Setting up official OpenVPN repository...
> apt-get update
> apt-get install -y ca-certificates curl
> mkdir -p /etc/apt/keyrings
> curl -fsSL https://swupdate.openvpn.net/repos/repo-public.gpg -o /etc/apt/keyrings/openvpn-repo-public.asc
[INFO] Updating package lists with new repository...
> apt-get update
[INFO] OpenVPN official repository configured
[INFO] Installing OpenVPN and dependencies...
> apt-get install -y openvpn iptables openssl curl ca-certificates tar dnsutils socat
[INFO] Data Channel Offload (DCO) is not available (requires OpenVPN 2.6+ and kernel support)
> mkdir -p /etc/openvpn/server
> curl -fL --retry 5 -o /tmp/easy-rsa.yQUTEh.tgz https://github.com/OpenVPN/easy-rsa/releases/download/v3.2.6/EasyRSA-3.2.6.tgz
[INFO] Verifying Easy-RSA checksum...
> mkdir -p /etc/openvpn/server/easy-rsa
> tar xzf /tmp/easy-rsa.yQUTEh.tgz --strip-components=1 --no-same-owner --directory /etc/openvpn/server/easy-rsa
> rm -f /tmp/easy-rsa.yQUTEh.tgz
[INFO] Initializing PKI...
> ./easyrsa init-pki
[INFO] Building CA...
> ./easyrsa --batch --req-cn=cn_GNUS7ZXWa9jbNeUp build-ca nopass
[INFO] Building server certificate...
> ./easyrsa --batch build-server-full server_FWHHAlJUejNIBktT nopass
> ./easyrsa gen-crl
[INFO] Generating TLS key...
> openvpn --genkey tls-crypt-v2-server /etc/openvpn/server/tls-crypt-v2.key
[INFO] Copying certificates...
> cp pki/ca.crt pki/private/ca.key pki/issued/server_FWHHAlJUejNIBktT.crt pki/private/server_FWHHAlJUejNIBktT.key /etc/openvpn/server/easy-rsa/pki/crl.pem /etc/openvpn/server
> chmod 644 /etc/openvpn/server/crl.pem
[INFO] Generating server configuration...
> mkdir -p /etc/openvpn/server/ccd
> mkdir -p /var/log/openvpn
[INFO] Enabling IP forwarding...
> mkdir -p /etc/sysctl.d
> sysctl --system
[INFO] Configuring OpenVPN service...
> cp /usr/lib/systemd/system/openvpn-server@.service /etc/systemd/system/openvpn-server@.service
> sed -i s|LimitNPROC|#LimitNPROC| /etc/systemd/system/openvpn-server@.service
> sed -i /\[Service\]/a RuntimeDirectory=openvpn-server /etc/systemd/system/openvpn-server@.service
> systemctl daemon-reload
> systemctl enable openvpn-server@server
> systemctl restart openvpn-server@server
[INFO] Configuring firewall rules...
> mkdir -p /etc/iptables
> chmod +x /etc/iptables/add-openvpn-rules.sh
> chmod +x /etc/iptables/rm-openvpn-rules.sh
> systemctl daemon-reload
> systemctl enable iptables-openvpn
> systemctl start iptables-openvpn
[INFO] Creating client template...
[INFO] Generating first client certificate...
[INFO] Generating client certificate...
> ./easyrsa --batch build-client-full vpnclient nopass
[OK] Client vpnclient added and is valid for 3650 days.
> cp /etc/openvpn/server/client-template.txt /root/vpnclient.ovpn
[OK] The configuration file has been written to /root/vpnclient.ovpn.
[INFO] Download the .ovpn file and import it in your OpenVPN client.
[OK] If you want to add more clients, you simply need to run this script another time!
client
proto tcp-client
remote 49.12.68.126 443
dev tun
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
verify-x509-name server_FWHHAlJUejNIBktT name
auth SHA256
auth-nocache
cipher AES-128-GCM
ignore-unknown-option data-ciphers
data-ciphers AES-128-GCM
ncp-ciphers AES-128-GCM
tls-client
tls-version-min 1.2
tls-cipher TLS-ECDHE-ECDSA-WITH-AES-128-GCM-SHA256
tls-ciphersuites TLS_AES_256_GCM_SHA384:TLS_AES_128_GCM_SHA256:TLS_CHACHA20_POLY1305_SHA256
ignore-unknown-option block-outside-dns
setenv opt block-outside-dns # Prevent Windows 10 DNS leak
verb 3
<ca>
-----BEGIN CERTIFICATE-----
MIIB2jCCAYCgAwIBAgIUaVbim3jbv1dkXGrud/3W57aHmU8wCgYIKoZIzj0EAwIw
HjEcMBoGA1UEAwwTY25fR05VUzdaWFdhOWpiTmVVcDAeFw0yNjA1MTcwNDM2MDFa
Fw0zNjA1MTQwNDM2MDFaMB4xHDAaBgNVBAMME2NuX0dOVVM3WlhXYTlqYk5lVXAw
WTATBgcqhkjOPQIBBggqhkjOPQMBBwNCAAQFjf7Q7Fl/63Xi7y22Irs4O1TbiKoS
fH8cCXG0bx13mrKgksCKHMDJz6J+ND1N9AhJ+6C1av1ec+2uqaAGjn8xo4GbMIGY
MA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYEFNnplEQHDGaG8griMJGdtRZ7pgUp
MFkGA1UdIwRSMFCAFNnplEQHDGaG8griMJGdtRZ7pgUpoSKkIDAeMRwwGgYDVQQD
DBNjbl9HTlVTN1pYV2E5amJOZVVwghRpVuKbeNu/V2Rcau53/dbntoeZTzALBgNV
HQ8EBAMCAQYwCgYIKoZIzj0EAwIDSAAwRQIgcSOK1+kGj0/p38gQKdxYgTRAT7my
RmzW8gvDfJX/FKkCIQDQAfDJE6023bGfPXzp1Bb4NW+xFBr5hNUodGooFBwM1A==
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
MIIB3TCCAYKgAwIBAgIRALRJzRtu2TzIjoiPz0KSF1UwCgYIKoZIzj0EAwIwHjEc
MBoGA1UEAwwTY25fR05VUzdaWFdhOWpiTmVVcDAeFw0yNjA1MTcwNDM2MDJaFw0z
NjA1MTQwNDM2MDJaMBQxEjAQBgNVBAMMCXZwbmNsaWVudDBZMBMGByqGSM49AgEG
CCqGSM49AwEHA0IABAFWmeTJvlDNqUDha+ImJ2RRjqsbwzbBaRqK+j6JgsdJMqpF
Ksv9K3tyWdAz33r5rAImTNlbKkhGKVp15JqdUkijgaowgacwCQYDVR0TBAIwADAd
BgNVHQ4EFgQU3LaQ6tYsM1k2u97V8fDDs8oXrhowWQYDVR0jBFIwUIAU2emURAcM
ZobyCuIwkZ21FnumBSmhIqQgMB4xHDAaBgNVBAMME2NuX0dOVVM3WlhXYTlqYk5l
VXCCFGlW4pt4279XZFxq7nf91ue2h5lPMBMGA1UdJQQMMAoGCCsGAQUFBwMCMAsG
A1UdDwQEAwIHgDAKBggqhkjOPQQDAgNJADBGAiEA6Pft4tWFK8NwfMWtP7KD3UnY
raw/P1RyfO49T1sD4bcCIQCCksiMc8Q2fh+q+0Flfz0lHKGtz5lLAScOvfuV4axH
Pg==
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
MIGHAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBG0wawIBAQQgt9k+GjSUEpYhEIxL
6QZrTRO+7O9EvIJIxMgza2f8sFWhRANCAAQBVpnkyb5QzalA4WviJidkUY6rG8M2
wWkaivo+iYLHSTKqRSrL/St7clnQM996+awCJkzZWypIRiladeSanVJI
-----END PRIVATE KEY-----
</key>
<tls-crypt-v2>
-----BEGIN OpenVPN tls-crypt-v2 client key-----
Sz5dqksyS4Baghl1x0bSI7B5wCrlovPuLU9lWnzEXUl3dFXhnvEVf5i2NZl0btcS
1rlq48Q3XMXgtR5Lvd14oYnPTlCgPTdkvKZ8MvDKCIQfYJbxRXKjqZqELFuPhQc+
Y19c8GJRCKalmZGbQzFHUJ3rPA9FKlTt6w6PhJLVcpGKxZ/hmVOVQ8Ashm4b8j++
VCfhUWBPgoDFA2Zgop64whOS8dYqFLJKuxX9ex7iyjHEOHG8yNgz78/IG+4RVvy7
QFO/5ta8J19GygBGr/5EKZRihp2UD4DqfzajwJ9wBcIJ2jf8hGcla+F9G+FcLbZV
BUiNOxN1WVVdhnhR8VjZmiYrk0ABqwybpiUuYoqZkKJAjWot7bLZEUtW/uAS7Pop
ETaNaBuow4JRhGJXNt1WL5aX9bzh7P9Z51qGSAKlTSwy2cCUEwxaV9Mq6oV7GIzh
0bX3A0WpiWNAxM2lsV0cPUhWplZrI6dXUH5EAoagiYeXIWUzGdRUGtu5IZ+aMWNW
f310OhQ23CTfMf6j5fsVuKlaQ8LmQZz/b9SPFJrAwUJXkUQgFKxxzM90bEW/9ofa
vhAFxckMWSS0aeBqvTZ8DihPOqDwEaCciy1a6PT1bKOQr8XIdQv+NUc+pSD7R5M7
3Ic/wJTe8DcMnS1ZEm9Y4yoGbFbmbPCrCOOK/iiMUTFiapAFFa0r3mxgfxY8/0k3
t1CPmN23+6nfCi8i4XdMwEfSHwvKvFm5yQEr
-----END OpenVPN tls-crypt-v2 client key-----
</tls-crypt-v2>
```

## Exit Code: 0
