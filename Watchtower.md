# Watchtower Compose Install

``` yaml
version: "3"
services:
  watchtower:
    image: containrrr/watchtower:latest
    container_name: watchtower
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    environment:
      - TZ=America/Toronto
      - WATCHTOWER_CLEANUP=true
      - WATCHTOWER_SCHEDULE=0 0 0 * * 1
      - WATCHTOWER_INCLUDE_STOPPED=true
      - WATCHTOWER_REVIVE_STOPPED=false
    restart: unless-stopped
```

