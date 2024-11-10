After setting up the AWS SES API, you may see the following message while debugging:

>Request to AWS SES API failed. Reason: An error occurred while executing "SendRawEmail" on "https://email.ap-northeast-2.amazonaws.com". AWS HTTP Error: cURL error 60: SSL certificate issue: Unable to retrieve local issuer certificate for https://email.ap-northeast-2.amazonaws.com (see https://curl.haxx.se/libcurl/c/libcurl-errors.html)"

In this case, update your certificate to the latest one.

## To update, do the following:
1. Download the latest certificate file `cacert.pem` from https://curl.se/docs/caextract.html to an appropriate location. (In my case, I downloaded it to D:\app\apache\Apache24\conf\ssl.)

2. Open `php.ini` and update the certificate path.
```
[curl]
curl.cainfo = "D:\app\apache\Apache24\conf\ssl\cacert.pem"

[openssl]
openssl.cafile="D:\app\apache\Apache24\conf\ssl\cacert.pem"
```

3. Restart the server.
