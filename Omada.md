# Omada Compose Install

``` yaml
version: "3.1"

services:
  omada-controller:
    container_name: omada-controller
    hostname: omada
    image: mbentley/omada-controller:latest
    restart: unless-stopped
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.33
    environment:
      - MANAGE_HTTP_PORT=8088
      - MANAGE_HTTPS_PORT=8043
      - PGID=508
      - PORTAL_HTTP_PORT=8088
      - PORTAL_HTTPS_PORT=8043
      - PUID=508
      - SHOW_SERVER_LOGS=true
      - SHOW_MONGODB_LOGS=false
      - SSL_CERT_NAME=tls.crt
      - SSL_KEY_NAME=tls.key
      - TZ=America/Toronto
    volumes:
      - omada-data:/opt/tplink/EAPController/data
      - omada-work:/opt/tplink/EAPController/work
      - omada-logs:/opt/tplink/EAPController/logs

networks:
  macvlan_network:
    external:
      name: macvlan_network

volumes:
  omada-data:
  omada-work:
  omada-logs:
```

