# Reference of most commonly used OpenSSL commands
1. Create certificate
2. Verify certs and keys
3. Hash and fingerprint
4. Encryption and decryption
5. Debugging

## 1. Create Certificate {#1}
Generate a private 4096-bit RSA key.
```console
$ openssl genrsa -out private.key 4096
```

Generate a signing request (CSR) with SHA256 signature and valid for 1 year.
```console
$ openssl req -new -key private.key -days 365 -sha256 -out file.csr
```

Generate an RSA private key with default parameters.
```console
$ openssl genpkey -algorithm RSA -out private_key.pem
```

Then, to extract the pair's public key from the private key.
```console
$ openssl rsa -in private_key.pem -outform PEM -pubout -out public_key.pem
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA1JHyxBl5XibQ/lyB4Di7
XLERG1AOeiwAwZVpvW85qOhvcV1AdKpcqcy9Qh86ysmgG7JwEmCMIIF8uGv2hN1d
HsoACwhRU3aquX00UPDXz49YyImfOZVaLeNiACQ58KuJYAF6CdTVF9e87nuMF+Yx
wlmHae4cCvAHDtSFt4JEf5veTQPhgRDmlKVw59ci41yxfzUAS5VQph1R6nX3qvYe
BhTrr5gLBJ7y0dTT3GI2Gb4F1AWB6gjehDgiRBLpGNbNXsX363COlcIVDJhb1tHd
1D2y1vD0C4yr6RdbV5ws5YcaL6vIlwJmPOWUSfe0bBuuvhOOU2t+bn5zJxrLen4N
mwIDAQAB
-----END PUBLIC KEY-----
```

## 2. Verify Certs and Keys
Check on a certificate file.
```console
$ openssl x509 -text -noout -in file.crt
```

Check on the detail of a certificate signing request (CSR)
```console
$ openssl req -verify -text -noout -in file.csr
```

Check on validity of a private key.
```console
$ openssl rsa -check -text -noout -in private.key
```

Check on the certificate revocation list (CRL).
```console
$ openssl crl -text -noout -in file.pem
```

## 3. Hash and Fingerprint
Generate MD5 hash from stdin, or file.
```console
$ echo -n "Hello World" | openssl dgst -md5
MD5(stdin)= b10a8db164e0754105b7a99be72e3fe5
$ echo -n "Hello World" | openssl md5
MD5(stdin)= b10a8db164e0754105b7a99be72e3fe5
$ openssl sha1 file.csr
SHA1(file.csr)= 15d0df9d69683fbe232fbf2d2c5a3873763d339c
```

|      | Hash Algorithm | Description      |
| ---: | :------- | :--------------- |
| 1    | md4  |  |
| 2    | md5    |  |
| 3    | mdc2    |  |
| 4    | ripemd160  |   |
| 5    | sha  |  |  
| 6    | sha1     |  |  
| 7    | sha256     |  |  
| 8    | sha384     |  |  
| 9    | sha512     |  |  
| 10   | whirpool     |  |  

To retrieve the fingerprint of a certificate.
```console
$ openssl x509 -noout -fingerprint -sha256 -inform der -in www.google.com.crt
sha256 Fingerprint=EB:45:33:D6:01:18:E6:D2:09:50:B8:AE:22:84:2E:51:75:0E:1D:26:3A:60:8B:B3:98:02:13:65:95:95:77:9C
$ openssl x509 -noout -fingerprint -sha256 -inform PEM -in www.google.com.pem
sha256 Fingerprint=EB:45:33:D6:01:18:E6:D2:09:50:B8:AE:22:84:2E:51:75:0E:1D:26:3A:60:8B:B3:98:02:13:65:95:95:77:9C
```

## 4. Encryption and Decryption
To get a list of available ciphers.
```console
$ openssl list -cipher-commands
$ openssl list -cipher-algorithms
```

General used on encrypting a file.
``` openssl aes-256-cbc [-a] -in INPUT_FILE -out ENCRYPTED_FILE [-pass KEY:VALUE]```

To encrypt a file.
```console
$ openssl enc -aes-256-cbc -in plain.txt -out file.enc
```

To encrypt a file with password file.
```console
$ openssl aes-256-cbs -in plain.txt -out file.enc -pass file:password.txt
```

General used on decrypting a file.
``` openssl aes-256-cbc -d [-a] -in ENCRYPTED_FILE -out OUTPUT_FILE [-pass KEY:VALUE] [-md md5]```

Tp decrypt a file with specified password.
```console
$ openssl aes-256-cbc -d -in file.enc -out decrypted.txt -pass pass:mySuperSecretPassword
```

To decrypt an encrypted file and generate Base64 encoded output
```console
$ openssl aes-256-cbc -d -a -in file.enc -out decrypted.txt 
```

## 5. Debugging
To download a certificate from a web site.
```console
$ echo "Q" | openssl s_client -connect www.google.com:443 -showcerts | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > www.google.com.pem
```

To convert a certificate from PEM format to DER format.
```console
$ openssl x509 -inform PEM -in www.google.com.pem -outform DER -out www.google.com.crt
```

Test a connection, certificate chain, protocol and cipher negotiation.
```console
$ openssl s_client -connect hostname:port
```

To test a connection within script.
```console
$ echo "Q" | openssl s_client -connect www.google.com:443
$ echo "Q" | openssl s_client -connect www.google.com:443 -showcerts
```

To get version info.
```console
$ openssl version -a                                                                                                                                 130 ⨯
OpenSSL 3.0.2 15 Mar 2022 (Library: OpenSSL 3.0.2 15 Mar 2022)
built on: Thu Oct 27 17:06:56 2022 UTC
platform: debian-amd64
options:  bn(64,64)
compiler: gcc -fPIC -pthread -m64 -Wa,--noexecstack -Wall -Wa,--noexecstack -g -O2 -ffile-prefix-map=/build/openssl-WsPfAX/openssl-3.0.2=. -flto=auto -ffat-lto-objects -flto=auto -ffat-lto-objects -fstack-protector-strong -Wformat -Werror=format-security -DOPENSSL_TLS_SECURITY_LEVEL=2 -DOPENSSL_USE_NODELETE -DL_ENDIAN -DOPENSSL_PIC -DOPENSSL_BUILDING_OPENSSL -DNDEBUG -Wdate-time -D_FORTIFY_SOURCE=2
OPENSSLDIR: "/usr/lib/ssl"
ENGINESDIR: "/usr/lib/x86_64-linux-gnu/engines-3"
MODULESDIR: "/usr/lib/x86_64-linux-gnu/ossl-modules"
Seeding source: os-specific
CPUINFO: OPENSSL_ia32cap=0xfffa32235f8bffff:0x184007a4219c27ab
```
