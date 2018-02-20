---
layout: post
---

Wanted to setup stunnel for client certificates and it took me longer than expected so noting here
for future reference.  Here's the contents of the stunnel.conf I put in the current directory.

This isn't the most recent configuration

    client = yes
    verify = 2
    debug = 7
    output = /dev/stdout
    # doesn't like relative path
    pid = /tmp/stunnel.pid
    [master]
    accept = 127.0.0.1:1443
    connect = server:443
    cert = client_crt_key.pem
    key = client_crt_key.pem
    CAfile = /etc/pki/tls/certs/ca-bundle.crt

While compiling the config I noticed there are some newer parameters but this worked on the version
I had.  Then run with:

    stunnel ./stunnel.conf
