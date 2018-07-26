## Proxy a local port to a local port on a remote host

```
ssh -L 9200:localhost:9200 -N remote-host.example.com
```

Accessing `localhost:9200` will be forwarded as a local connection on `remote-host.example.com`.