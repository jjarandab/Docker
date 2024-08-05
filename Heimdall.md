# Heimdall Compose Install

``` yaml
version: "2.1"
services:
  heimdall:
    image: lscr.io/linuxserver/heimdall:latest
    container_name: heimdall
    hostname: heimdall
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.34
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Toronto
    volumes:
      - heimdall:/config
    ports:
      - 80:80
      - 443:443
    restart: unless-stopped
volumes:
  heimdall:
    external: false
networks:
  macvlan_network:
    external:
      name: macvlan_network
```

