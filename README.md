### Goal
- Create a simple apache web server that serves different content based on the domain name used to access it.
- Create self-signed certificate for TLS/SSL encryption.
- Redirect HTTP to HTTPS.
- Setup a custom logging format.

### add in /etc/hosts of local machine:
```bash
127.0.0.1 a.com
127.0.0.1 b.com
```

### We'll make use of self-signed certificate for SSL encryption like this:
**Create a self-signed certificate using OpenSSL:**
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout key-a.pem -out cert-a.pem
# next in the prompt, use whatever value for all fields except Common Name, which should be the FQDN or public IP of your server, aka a.com
# do the same for b.com
```
[Source for above.](https://ubiq.co/tech-blog/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-debian/)

Make the necessary changes in the docker-compose.yaml, websites content and the httpd.conf according to your usecase.

### in browser, type:
a.com
b.com

Continue in browser if it says that the certificate is not trusted because this is a self-signed certificate just for demo purposes. In production, you should use a certificate from a trusted CA.

---

Now, we can use the same apache web server to serve different content based on the domain name used to access it, with SSL encryption and custom logging format.