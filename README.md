# ODL Musings


## To build ODL docker container

Edit Dockerfile ENV parameters according to the ODL release and basename ("karaf" or "opendaylight", certain older releases use "karaf" as the basename).

```
ENV basename karaf
ENV release 0.8.4
```


```
docker build -t mbound/opendaylight:0.10.0 .
```

## To run ODL docker container

With host network:
```
docker run -t -d --network host --name odl1 mbound/opendaylight:0.10.0
```

With docker network:
```
docker run -t -d --name odl1 mbound/opendaylight:0.10.0
```

## Now let's log into ODL

With host network:
```
ssh -p 8101 karaf@localhost
```

With docker network:
```
ssh -p 8101 karaf@`docker-ip odl1`
```

