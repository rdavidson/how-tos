# Creating the a new self signed cert.
This page describes the process to create a new self signed cert. This can be use with ELB to provide SSL.


Create new private key
```
openssl genrsa -out my-private-key.pem 2048

```


The next step is to create a Certificate Signing Request (CSR). This is a file that you can send to a certificate authority (CA) to apply for a server certificate.

To create a CSR:
```
openssl req -sha256 -new -key my-private-key.pem -out csr.pem

```

To create the self signed cert
```
openssl x509 -req -days 365 -in csr.pem -signkey my-private-key.pem -out my-certificate.pem
```