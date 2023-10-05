# CREATE THE .MOBILECONFIG FILE


```<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>PayloadContent</key>
    <dict>
        <key>URL</key>
        <string><!-- URL to send the response to --></string>
        <key>DeviceAttributes</key>
        <array>
            <string>UDID</string>
            <string>IMEI</string>
            <string>ICCID</string>
            <string>VERSION</string>
            <string>PRODUCT</string>
        </array>
    </dict>
    <key>PayloadOrganization</key>
    <string><!-- a DNS-style name for the organization requesting (e.g., example.com) --></string>
    <key>PayloadDisplayName</key>
    <string><!-- a human-readable name for this request --></string>
    <key>PayloadVersion</key>
    <integer>1</integer>
    <key>PayloadUUID</key>
    <string><!-- a UUID-formatted unique identifier for this request (e.g., D77DD928-4312-4E9E-9562-690D695EC7CD) --></string>
    <key>PayloadIdentifier</key>
    <string><!-- a reverse DNS-formatted identifier for this request (e.g., com.example.profile-request) --></string>
    <key>PayloadDescription</key>
    <string><!-- a human-readable description of what this request is for --></string>
    <key>PayloadType</key>
    <string>Profile Service</string>
</dict>
</plist>
```




# SIGN THE .MOBILECONFIG FILE

```openssl smime -sign -signer <your ssl certificate file> -inkey <your private key file> -certfile <additional certificates if your issuer provides them> -nodetach -outform der -in <the basic .mobileconfig to sign> -out <the output file to save it as>
```

# DELIVER THE .MOBILECONFIG FILE
### Content-Type Header
```application/x-apple-aspen-config
```

# VERIFIY KEYS (OPTIONAL)
```
openssl x509 -noout -modulus -in server.crt | openssl md5
openssl rsa -noout -modulus -in server.key | openssl md5
```


## Source
https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/iPhoneOTAConfiguration/OTASecurity/OTASecurity.html#//apple_ref/doc/uid/TP40009505-CH3-SW1