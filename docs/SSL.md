## Fetch the contents of an SSL certificate

```
echo | openssl s_client -showcerts -connect github.com:443 2>/dev/null | openssl x509 -text
```

(the initial `echo` closes the client, otherwise it stays open waiting on input)

To extract a part of the cert, check the `openssl` flags. For example, to extract the issuer:

```
$> echo | openssl s_client -showcerts -connect github.com:443 2>/dev/null | openssl x509 -issuer -noout
issuer= /C=US/O=DigiCert, Inc./CN=DigiCert High Assurance TLS Hybrid ECC SHA256 2020 CA1
```

(`-noout` prevents the certificate content from being included in the output)
