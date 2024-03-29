# Nginx: Reverse Proxy

### Configuration File

The nginx config file is located on: `/etc/nginx/conf.d/default.conf`

### Working As Reverse Proxy

To work as reverse poroxy inside the config file it's necessary the following rules:

```
location {
   proxy_pass http://<address>;
}
```

### Working As Load Balancer

To work as load balancer inside the config file it's necessary the following rules:

- create a server group

```
upstream <upstream-name> {
   server <address1>;
   server <address2>;
}
```

- setup the server group

```
location {
   proxy_pass http://<upstream-name>;

   # forward the real request ip address
   proxy_set_headers X-Header-Name $remote_addr;
}
```

**Obs:** Inside the workers on `/etc/nginx/nginx.conf` it's necessary to put the header inside the object `http` on
log_format

### Supplementary Resources

- [Official Docs](https://nginx.org/en/)

