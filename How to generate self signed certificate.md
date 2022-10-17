# How to Generate self signed certificate

You can create self signed certificate for test security HTTPS on your Web server
For wildcard SSL

Command: 
```
openssl genrsa -out <Yourname_Private>.key

openssl req -new -key <Yourname_Private>.key -out <Yourname_Request>.csr

openssl x509 -req -days 365 -in <Yourname_Request>.csr -signkey <Yourname_Private>.key -out <Yourname_Cert>.crt
```

After create file all
- private.key
- request.csr
- cert.crt

Convert PEM to .PFX

Command:
```
openssl pkcs12 -export -out <Yourname>.pfx -inkey <Yourname_Private>.key -in <Yourname_Cert>.crt
```
Ref. https://www.sslshopper.com/ssl-converter.html


# Add Intermediate Cert to .PFX file
You must download Intermediate Cert from  Certificate Provider

Command: 
```
openssl pkcs12 -export -out <Yourname>.pfx -inkey <Yourname_Private>.key -in certificate.crt -certfile <Your_Intermediate>.crt
```
Ref. https://www.ssl.com/how-to/create-a-pfx-p12-certificate-file-using-openssl/


# Add Keystore .JKS to .PFX file
Case file .jks import to .pfx

Command: 
```
“$JAVA_HOME/bin/keytool -importkeystore -destkeystore <Yourname>.jks -srckeystore <Yourname>.pfx -srcstoretype pkcs12 -alias <YourDomain>”
```