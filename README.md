# http-session-counter

This is a session counter example taken from JBoss EAP demos.

I couldn't find this readily available on Github, so I posted a copy to my own repo.

https://access.redhat.com/solutions/46373

Once the application is deployed, you can curl the `/counter` endpoint with a `JSESSIONID` to increment the counter.  The cache is configured to replicate its state to all other servers.

```bash
curl -v http://<server>:8080/counter --header "Cookie: JSESSIONID=ueRgXKhBFRjRubmyzF5z2LjZZIdJzi_nG2zUA-2y"
```




## OpenShift

When deployed on OpenShift, the `Route` can be configured to round-robin if you want to see requests landing on different servers.

Set this annotation `haproxy.router.openshift.io/balance` on the 'Route' to one of the following values

- roundrobin
- leastconn
- source
