# MIGRATE CONTAINER

``` bash
docker stop NAME_OF_INSTANCE
docker commit NAME_OF_INSTANCE mycontainerimage
docker save mycontainerimage | gzip > mycontainerimage.tar.gz
gunzip -c mycontainerimage.tar.gz | docker load
docker run -d --name=PICK_NAME_FOR_CONTAINER mycontainerimage
```

optional

``` bash
docker save mycontainerimage | gzip | ssh root@203.0.113.1 'gunzip | docker load'31
```

