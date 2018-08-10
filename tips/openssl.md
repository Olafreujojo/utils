# OpenSSL
- [OpenSSL](#openssl)

## Get certificate with s_client
```
echo "EXIT" | openssl s_client -connect host:port -showcerts | openssl x509 -noout -text
```
Other parameters:
-   `-proxy proxyhost:port`
-   `-servername www.servername.com` : take care of SNI