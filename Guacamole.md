# Guacamole Compose Install

``` yaml
version: "2.1"
services:
  guacamole:
    image: jwetzell/guacamole:latest
    container_name: guacamole
    hostname: guacamole
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.46
    volumes:
      - guacamole:/config
    ports:
      - 8080:8080
    environment:
      - EXTENSIONS=auth-totp
    restart: unless-stopped
volumes:
  guacamole:
    external: false
networks:
  macvlan_network:
    external:
      name: macvlan_network
```

