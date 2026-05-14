# Germany Server - Thu May 14 12:22:19 UTC 2026

## Command: `cat /root/vpnclient.ovpn`
```
Warning: Permanently added '78.47.70.169' (ED25519) to the list of known hosts.
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
```

## Exit Code: 0
