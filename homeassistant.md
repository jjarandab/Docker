# Home Assistant

``` bash
docker run --init --name homeassistant --net=host --privileged -itd -v /portainer/Files/AppData/Config/Prometheus/HomeAssistant:/config -e TZ=America/Toronto homeassistant/home-assistant:stable
```

