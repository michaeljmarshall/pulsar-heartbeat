# Pulsar Operation Monitoring

This is a ops monitoring tool for
- monitoring Pulsar admin tenants endpoint
- measure message latency from producing to consuming
- report and monitor heartbeat with OpsGenie

This is a data driven tool. The configuraion data is at ./config/runtime.json

## Docker
The runtime.json file must be mounted as /app/runtime.json

This runs a multi stage build that produces a 18MB docker image.
```
$ sudo docker build -t pular-ops-monitor .
```

``` bash
$ sudo docker run -d -it -v /home/ming/go/src/gitlab.com/operation-monitor/config/runtime.json:/config/runtime.json -v /etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem:/etc/ssl/certs/ca-bundle.crt --name=pulsar-monitor pular-ops-monitor
```