### Goal
- Create a simple apache web server that serves different content based on the domain name used to access it.
- Create self-signed certificate for TLS/SSL encryption.
- Redirect HTTP to HTTPS.
- Setup a custom logging format.

### in local machine: /etc/hosts
127.0.0.1 a.com
127.0.0.1 b.com

### in browser, type:
a.com
b.com

### We'll make use of self-signed certificate for TLS/SSL encryption like this:
**Create a self-signed certificate using OpenSSL:**
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout key-a.pem -out cert-a.pem
# next in the prompt, use whatever value for all fields except Common Name, which should be the domain name/public IP of your server, aka a.com
# do the same for b.com
```
[Source for above.](https://ubiq.co/tech-blog/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-debian/)