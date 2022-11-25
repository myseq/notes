# Reference of most commonly used OpenSSL commands
1. Create certificate
2. Verify certs and keys
3. Hash
4. Encryption and decryption
5. Debugging

## 1. Create Certificate
Generate a private 4096-bit RSA key.
```console
$ openssl genrsa -out private.key 4096
```

Generate a signing request (CSR) with SHA256 signature and valid for 1 year.
```console
$ openssl req -new -key private.key -days 365 -sha256 -out file.csr
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

## 3. Hash
Generate MD5 hash from stdin, or file.
```console
$ echo -n "Hello World" | openssl md5
$ openssl sha1 file.csr
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


## 4. Encryption and decryption


## 5. Debugging
Test a connection, certificate chain, protocol and cipher negotiation.
```console
$ openssl s_client -connect hostname:port
```

To test a connection within script.
```console
$ echo "Q" | openssl s_client -connect www.google.com:443
```
