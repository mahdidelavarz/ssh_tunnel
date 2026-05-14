# Germany Server - Thu May 14 13:32:41 UTC 2026

## Command: `cd /root && sudo ./openvpn-install.sh uninstall --force && rm -f openvpn-install.sh && curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh && chmod +x openvpn-install.sh && sudo ./openvpn-install.sh install --client vpnclient --port 443 --protocol tcp && cat /root/vpnclient.ovpn`
```
Warning: Permanently added '78.47.70.169' (ED25519) to the list of known hosts.

=== Remove OpenVPN ===

[INFO] Stopping OpenVPN service...
> systemctl disable openvpn-server@server
> systemctl stop openvpn-server@server
> rm -f /etc/systemd/system/openvpn-server@.service
[INFO] Removing firewall rules...
> systemctl stop iptables-openvpn
> systemctl disable iptables-openvpn
> rm /etc/systemd/system/iptables-openvpn.service
> systemctl daemon-reload
> rm -f /etc/iptables/add-openvpn-rules.sh
> rm -f /etc/iptables/rm-openvpn-rules.sh
[INFO] Removing OpenVPN package...
> apt-get remove --purge -y openvpn
> rm /etc/apt/sources.list.d/openvpn-aptrepo.list
> rm /etc/apt/keyrings/openvpn-repo-public.asc
> apt-get update
> find /home/ -maxdepth 2 -name *.ovpn -delete
> find /root/ -maxdepth 1 -name *.ovpn -delete
> rm -rf /etc/openvpn
> rm -rf /usr/share/doc/openvpn*
> rm -f /etc/sysctl.d/99-openvpn.conf
> rm -rf /var/log/openvpn
[OK] OpenVPN removed!
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0100  144k  100  144k    0     0   423k      0 --:--:-- --:--:-- --:--:--  423k
[INFO] === OpenVPN Non-Interactive Install ===
[INFO] Running in non-interactive mode with the following settings:
[INFO]   ENDPOINT=78.47.70.169
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
> curl -fL --retry 5 -o /tmp/easy-rsa.LZL5vw.tgz https://github.com/OpenVPN/easy-rsa/releases/download/v3.2.6/EasyRSA-3.2.6.tgz
[INFO] Verifying Easy-RSA checksum...
> mkdir -p /etc/openvpn/server/easy-rsa
> tar xzf /tmp/easy-rsa.LZL5vw.tgz --strip-components=1 --no-same-owner --directory /etc/openvpn/server/easy-rsa
> rm -f /tmp/easy-rsa.LZL5vw.tgz
[INFO] Initializing PKI...
> ./easyrsa init-pki
[INFO] Building CA...
> ./easyrsa --batch --req-cn=cn_UjjuuPzZ8sg5dd0m build-ca nopass
[INFO] Building server certificate...
> ./easyrsa --batch build-server-full server_SLVVOQlDLREaWnLF nopass
> ./easyrsa gen-crl
[INFO] Generating TLS key...
> openvpn --genkey tls-crypt-v2-server /etc/openvpn/server/tls-crypt-v2.key
[INFO] Copying certificates...
> cp pki/ca.crt pki/private/ca.key pki/issued/server_SLVVOQlDLREaWnLF.crt pki/private/server_SLVVOQlDLREaWnLF.key /etc/openvpn/server/easy-rsa/pki/crl.pem /etc/openvpn/server
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
remote 78.47.70.169 443
dev tun
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
verify-x509-name server_SLVVOQlDLREaWnLF name
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
MIIB2jCCAYCgAwIBAgIUFw5AkcMkMXoMg9ItyYLeKL/cPYQwCgYIKoZIzj0EAwIw
HjEcMBoGA1UEAwwTY25fVWpqdXVQelo4c2c1ZGQwbTAeFw0yNjA1MTQxMzMzMTha
Fw0zNjA1MTExMzMzMThaMB4xHDAaBgNVBAMME2NuX1VqanV1UHpaOHNnNWRkMG0w
WTATBgcqhkjOPQIBBggqhkjOPQMBBwNCAARlBEFeEis+IhioQxmOlHJ0zhBjr8N0
agVpafT4uAfFMjUSVpFrSHO5rInj8H4brMmE7HdY7L24YGDx8UzQXVw9o4GbMIGY
MA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYEFP3TP0jpXFwRnTwdM8H488lmswM4
MFkGA1UdIwRSMFCAFP3TP0jpXFwRnTwdM8H488lmswM4oSKkIDAeMRwwGgYDVQQD
DBNjbl9Vamp1dVB6WjhzZzVkZDBtghQXDkCRwyQxegyD0i3Jgt4ov9w9hDALBgNV
HQ8EBAMCAQYwCgYIKoZIzj0EAwIDSAAwRQIhAN0+UF/2b3TX+9LKkG4/AdgJdfBg
4nGYKM42KyX6qU+FAiB2G0VgGjxvk+Cs+VzSPdVKXb0+vkCl9QGgN1+7H2OaTw==
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
MIIB2zCCAYGgAwIBAgIQBWJzptjiRTAL+2BnF4J1KjAKBggqhkjOPQQDAjAeMRww
GgYDVQQDDBNjbl9Vamp1dVB6WjhzZzVkZDBtMB4XDTI2MDUxNDEzMzMyMFoXDTM2
MDUxMTEzMzMyMFowFDESMBAGA1UEAwwJdnBuY2xpZW50MFkwEwYHKoZIzj0CAQYI
KoZIzj0DAQcDQgAEWZOB9HOLYdbxMSb7OyzPjumVcR0VAWmRorbSmsG4EWRlOLGd
ga9RxY10F7kVz90hPFESLeWbEjoo+zy/P7btYaOBqjCBpzAJBgNVHRMEAjAAMB0G
A1UdDgQWBBR2WEja+m8ePALf/I0B7vJE5uJtQjBZBgNVHSMEUjBQgBT90z9I6Vxc
EZ08HTPB+PPJZrMDOKEipCAwHjEcMBoGA1UEAwwTY25fVWpqdXVQelo4c2c1ZGQw
bYIUFw5AkcMkMXoMg9ItyYLeKL/cPYQwEwYDVR0lBAwwCgYIKwYBBQUHAwIwCwYD
VR0PBAQDAgeAMAoGCCqGSM49BAMCA0gAMEUCIQDlFtBFZCDE7MmfkRctQymLkBxf
sGdPZZHwv+B0wK4jCgIgDlzyKZY2oRp2wNYUTUCatQVf73O4jJdkULRGmVQRcv0=
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
MIGHAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBG0wawIBAQQgkANlN26ZnLt95tn9
XilatqFqAKhYlV4MHTnWUS5C8FahRANCAARZk4H0c4th1vExJvs7LM+O6ZVxHRUB
aZGittKawbgRZGU4sZ2Br1HFjXQXuRXP3SE8URIt5ZsSOij7PL8/tu1h
-----END PRIVATE KEY-----
</key>
<tls-crypt-v2>
-----BEGIN OpenVPN tls-crypt-v2 client key-----
ORsQyJfds/qmAEq4sY1v6INlFTa1W+cAZPRD8WssK3vNDqCkB5PW0URF8kd62xOt
0ubRYecMoFpzq8Pt2aPMx09fKA8OyImThYsu98sUi+6jQhaOYokqAK5BoU88JjUg
gn4ZPm5GOufg5EWOK1NBq7O0kpYAhVY5Uk0eIBwab2WN3dqUpqMj31EpgY8wd81e
ppawh7MJL80urwLXxzH5y2oCi7FbFKqruDRRp2zA3q+yGV5rPq+RWqjHlUffTFsr
P41NZ1+413Phpi5l+/w1M+ftIMRqRdGdEdDSVsznVmtPjG9r8vJ02px8vUGXmJyN
IW25g8H4XKjbCjcwMgW5BU85OKJXNGMIKsZV/dtq60rQT14GNuqf6V9pJfRm4wQr
jZf0VGC8j0D8cJu8wYJPk3JZzQ9a2ETj+5rzOj+2/otG4DsQgjAcYm97gJSRlhrE
MYJLcA8WFiUcw0V9Kvk/sDNY9pmCFtJbAqWBm7q5RBTvL2mADJ+sgSMsrHbMiAtr
xA7meQ2NGrE2Fx9y9PbsZ9890LTY6jEa/iKBejfOkUve5f9w7RO2GTEORDcl9PnO
gM5j/5PwQsAgaKkAVarXgjrlA1kHNH1bqhVXRvgDBMdQIEyLHq5/cWn2oaOUEWCa
7bfLCMO56EGM70OobMfUQuH54QwwhPlZaoZedugs7dzxtiWL0OojrS2nN5/zd3v+
k3iJB+4rUM7vk3NEBQKQ8yj2gL5AUcDOrwEr
-----END OpenVPN tls-crypt-v2 client key-----
</tls-crypt-v2>
```

## Exit Code: 0
