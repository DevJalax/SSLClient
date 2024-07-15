## OpenSSL commands to generate keys and certificate for client and server (self-signed) [via OpenSSL]

1) openssl genrsa -out server.key 2048
2) openssl req -new -key server.key -out server.csr
3) openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
4) cat server.key > server.pem
5) cat server.crt >> server.pem
6) openssl pkcs12 -export -in server.pem -out keystore.pkcs12

similarly for client.

you can now import this pkcs12 file in chrome or any browser. since certificate is self signed , u will get untrusted ie chrome will say site is not safe then click proceed to url

## Uses of different file formats :

.pem: Generic container for various cryptographic data.
.cer/.cert: Store certificates.
.csr: Used to request certificates.
.key: Contains private keys.
.pkcs12: Bundle of cryptographic objects, usually including certificates and private keys.
