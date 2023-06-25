# TLS

## TLS exaplained

Every byte of a TLS connection explained and reproduced: [https://tls.ulfheim.net](https://tls.ulfheim.net)

## Server cert sign by custom CA

The CA consist of a root (private) key (i.e `root-ca.key`) and a public `root-ca.crt`.

The following script generates a server side certificate in the and signs it with the CA.

```bash
#!/bin/bash

# This scripts acts as a CA to issue a server-certificate.

# Generate a key for the particular services
openssl genrsa -out $1.key 2048 

# Generate que Sign request from the previouly generate key for a cusom common-name
openssl req -new -sha256 \
    -key $1.key \
    -subj "/C=US/ST=CA/O=Sec26, Inc./CN=$1.common.name" \
    -out $1.csr
#    -reqexts SAN \
#    -config <(cat /etc/ssl/openssl.cnf \
#        <(printf "\n[SAN]\nsubjectAltName=DNS:$1.common.name")) \

# Genrate the actual server-certificate and sign it with the root-ca.key (private) (u also need the root-ca.crt (public)
# that will be present in the clients in order to trust the generated server-certificate).
openssl x509 -req -in $1.csr \
    -CA root-ca.crt -CAkey root-ca.key -CAcreateserial \
    -out $1.crt -days 500 -sha256
```

The output should be something like: `./test.sh <name>`
```text
Generating RSA private key, 2048 bit long modulus
...........+++
..........+++
e is 65537 (0x10001)
Signature ok
subject=/C=US/ST=CA/O=Sec26, Inc./CN=<name>.common.name
Getting CA Private Key
```

