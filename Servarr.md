Servarr Compose Install

``` yaml
version: "2.1"

networks:
  macvlan_network:
    external:
      name: macvlan_network

volumes:
  radarr_hd:
    external: false
  radarr_uhd:
    external: false
  sonarr:
    external: false
  lidarr:
    external: false
  prowlarr:
    external: false
  bazarr:
    external: false

services:
  radarr_hd:
    image: lscr.io/linuxserver/radarr:latest
    container_name: radarr_hd
    hostname: radarr_hd
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.41
    environment:
      - PUID=0
      - PGID=0
      - TZ=America/Toronto
    volumes:
      - radarr_hd:/config
      - /media:/media
      - /downloads/hd:/downloads
    ports:
      - 7878:7878
    restart: unless-stopped

  radarr_uhd:
    image: lscr.io/linuxserver/radarr:latest
    container_name: radarr_uhd
    hostname: radarr_uhd
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.42
    environment:
      - PUID=0
      - PGID=0
      - TZ=America/Toronto
    volumes:
      - radarr_uhd:/config
      - /media:/media
      - /downloads/uhd:/downloads
    ports:
      - 7878:7878
    restart: unless-stopped

  sonarr:
    image: lscr.io/linuxserver/sonarr:latest
    container_name: sonarr
    hostname: sonarr
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.43
    environment:
      - PUID=0
      - PGID=0
      - TZ=America/Toronto
    volumes:
      - sonarr:/config
      - /media:/media
      - /downloads/hd:/downloads
    ports:
      - 8989:8989
    restart: unless-stopped

  lidarr:
    image: lscr.io/linuxserver/lidarr:latest
    container_name: lidarr
    hostname: lidarr
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.44
    environment:
      - PUID=0
      - PGID=0
      - TZ=America/Toronto
    volumes:
      - lidarr:/config
      - /media:/media
      - /downloads/hd:/downloads
    ports:
      - 8686:8686
    restart: unless-stopped

  prowlarr:
    image: lscr.io/linuxserver/prowlarr:develop
    container_name: prowlarr
    hostname: prowlarr
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.40
    environment:
      - PUID=0
      - PGID=0
      - TZ=America/Toronto
    volumes:
      - prowlarr:/config
      - /downloads/hd:/downloads
    ports:
      - 9696:9696
    restart: unless-stopped

  bazarr:
    image: lscr.io/linuxserver/bazarr:latest
    container_name: bazarr
    hostname: bazarr
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.45
    environment:
      - PUID=0
      - PGID=0
      - TZ=America/Toronto
    volumes:
      - bazarr:/config
      - /media:/media
      - /downloads/hd:/downloads
    ports:
      - 6767:6767
    restart: unless-stopped
```

