# Germany Server - Thu May 14 12:18:43 UTC 2026

## Command: `cd /root && rm -f openvpn-install.sh && curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh && chmod +x openvpn-install.sh && sudo ./openvpn-install.sh uninstall --force 2>/dev/null; sudo ./openvpn-install.sh install --client vpnclient && echo ===START_CONFIG=== && cat /root/vpnclient.ovpn && echo ===END_CONFIG=== && echo SUCCESS`
```
Warning: Permanently added '78.47.70.169' (ED25519) to the list of known hosts.
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0  5  144k    5  7736    0     0  29669      0  0:00:05 --:--:--  0:00:05 29639100  144k  100  144k    0     0   479k      0 --:--:-- --:--:-- --:--:--  480k
[INFO] === OpenVPN Non-Interactive Install ===
[INFO] Running in non-interactive mode with the following settings:
[INFO]   ENDPOINT=78.47.70.169
[INFO]   ENDPOINT_TYPE=4
[INFO]   CLIENT_IPV4=y
[INFO]   CLIENT_IPV6=n
[INFO]   VPN_SUBNET_IPV4=10.8.0.0
[INFO]   VPN_SUBNET_IPV6=fd42:42:42:42::
[INFO]   PORT=1194
[INFO]   PROTOCOL=udp
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
> curl -fL --retry 5 -o /tmp/easy-rsa.93Vp6G.tgz https://github.com/OpenVPN/easy-rsa/releases/download/v3.2.6/EasyRSA-3.2.6.tgz
[INFO] Verifying Easy-RSA checksum...
> mkdir -p /etc/openvpn/server/easy-rsa
> tar xzf /tmp/easy-rsa.93Vp6G.tgz --strip-components=1 --no-same-owner --directory /etc/openvpn/server/easy-rsa
> rm -f /tmp/easy-rsa.93Vp6G.tgz
[INFO] Initializing PKI...
> ./easyrsa init-pki
[INFO] Building CA...
> ./easyrsa --batch --req-cn=cn_4MIZWKmlCcedJURv build-ca nopass
[INFO] Building server certificate...
> ./easyrsa --batch build-server-full server_4GSnyTLD2nqP04vs nopass
> ./easyrsa gen-crl
[INFO] Generating TLS key...
> openvpn --genkey tls-crypt-v2-server /etc/openvpn/server/tls-crypt-v2.key
[INFO] Copying certificates...
> cp pki/ca.crt pki/private/ca.key pki/issued/server_4GSnyTLD2nqP04vs.crt pki/private/server_4GSnyTLD2nqP04vs.key /etc/openvpn/server/easy-rsa/pki/crl.pem /etc/openvpn/server
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
===START_CONFIG===
client
proto udp
explicit-exit-notify
remote 78.47.70.169 1194
dev tun
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
verify-x509-name server_4GSnyTLD2nqP04vs name
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
MIIB2jCCAYCgAwIBAgIUQKL29ow+Cdgq44eGKU2BjuXOr0EwCgYIKoZIzj0EAwIw
HjEcMBoGA1UEAwwTY25fNE1JWldLbWxDY2VkSlVSdjAeFw0yNjA1MTQxMjE5MTJa
Fw0zNjA1MTExMjE5MTJaMB4xHDAaBgNVBAMME2NuXzRNSVpXS21sQ2NlZEpVUnYw
WTATBgcqhkjOPQIBBggqhkjOPQMBBwNCAAQ9LbzZN/QahFFheQ3cJfRgRQ9l7M6n
MPdswk+OkCgbUvabblbG6j9pew8Dzxc/r0imXL2s1w2A1Zdu2R7xKm69o4GbMIGY
MA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYEFFIMkB14PGKvheU693CrldwCzzuV
MFkGA1UdIwRSMFCAFFIMkB14PGKvheU693CrldwCzzuVoSKkIDAeMRwwGgYDVQQD
DBNjbl80TUlaV0ttbENjZWRKVVJ2ghRAovb2jD4J2Crjh4YpTYGO5c6vQTALBgNV
HQ8EBAMCAQYwCgYIKoZIzj0EAwIDSAAwRQIgRjWnpwqxSg45xZvPW+7Y0MIaKYDD
1a/+gsFTDkupSdUCIQCOv7pXkD4pjtZq/bYl4q80kRS0mtyotIeaJxhJbt4/Aw==
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
MIIB2zCCAYGgAwIBAgIQF3fkd2oxbvzqdkEAHKLRjjAKBggqhkjOPQQDAjAeMRww
GgYDVQQDDBNjbl80TUlaV0ttbENjZWRKVVJ2MB4XDTI2MDUxNDEyMTkxNFoXDTM2
MDUxMTEyMTkxNFowFDESMBAGA1UEAwwJdnBuY2xpZW50MFkwEwYHKoZIzj0CAQYI
KoZIzj0DAQcDQgAE4A9JuJAgZxjynTc1s5Lwvj+9jSwr1CDO+TuFDa5w8HxGCUAu
MMjWx2tDuxwpE8upPTt/2Cf+aHV6qWOvm2YzzKOBqjCBpzAJBgNVHRMEAjAAMB0G
A1UdDgQWBBQKzCsNZrT7Y9S0vncuyAfMxmaNwTBZBgNVHSMEUjBQgBRSDJAdeDxi
r4XlOvdwq5XcAs87laEipCAwHjEcMBoGA1UEAwwTY25fNE1JWldLbWxDY2VkSlVS
doIUQKL29ow+Cdgq44eGKU2BjuXOr0EwEwYDVR0lBAwwCgYIKwYBBQUHAwIwCwYD
VR0PBAQDAgeAMAoGCCqGSM49BAMCA0gAMEUCIFc7VBR18aC6nCr6jXvFEZBz1i5I
1IUGIMizyMlEJa8iAiEA9JQZq3T0LsBOaafG18COxquA9Zb+I7633Gyi0Ddj4O8=
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
MIGHAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBG0wawIBAQQg7btlIqkvJ2Rn5xLb
awLC9a/1DMQ4nr4Wgv7KFG9QAyOhRANCAATgD0m4kCBnGPKdNzWzkvC+P72NLCvU
IM75O4UNrnDwfEYJQC4wyNbHa0O7HCkTy6k9O3/YJ/5odXqpY6+bZjPM
-----END PRIVATE KEY-----
</key>
<tls-crypt-v2>
-----BEGIN OpenVPN tls-crypt-v2 client key-----
9xYA/X2cAXIjGItiTKMh2+qx7brxlu6iE10aQiHEodPdiYRFKWunIdisLIsSsoZf
ztmNoKyyQwtu86E5bZuusMD0sUe9jzq2Ooo5A92KhyEamZfZmLRVghL/0troTti/
g7kQH9PAkB6o27WAS5gBO4PYShKadrOIaKDE+KVNhIjkpbAx+76LoU1uZ7wFia5L
xlSxbAlfXp+NbrsfzxW16Fe2dNn0csbZ8RrWzayyY0MrdHTgQl/D/v+lGcXdNyXY
LGnHJPbOJ5u7OMVjABwvdpXYt6PriI0AvkId1AjYYNQcw0c+0S0ZRrm7vWgPgfVF
xYnVMutfL6f35PZ1QoDMGgrd7hjPacqqC9U4xg+KaVMd4s8dnbYtLPmm2G8L1upk
njiTt9cRJTnilXaL9YRqyQIusM9SxMal5ho9znV60vgrRLrDG4HjvI46ZIB+kGym
o/gDuylXX5jO6qGvWfxiWqVvqT9/J+vWXPz09Ow1Vj6OOQUqY/6yQPqNsmEf8gJE
cY6myeRI0o9Lpo2LnvwSuyvjFmkobGrEfJQomajrLxJAcYsYr11koBv9YNW5xwr3
WIx0Ea0l4DDP28uNL4c9h71hTuBB2olEG0smSlJhi2Cl9HC3Jp/JsZT1/Vi/3IR8
6x5PoqBWtzxRB9D6pjGwdWQm4gE9+RXSF6xVclkUPB7CKOkkzo+JQWNQZpHlEVpY
qTfPpKN1tdy2PT6a1dyciAeU3i/8UBM0JgEr
-----END OpenVPN tls-crypt-v2 client key-----
</tls-crypt-v2>
===END_CONFIG===
SUCCESS
```

## Exit Code: 0
