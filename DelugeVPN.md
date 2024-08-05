# DelugeVPN Compose Install

``` yaml
version: '3.3'
services:
  deluge_hd:
    ports:
      - '8112:8112'
      - '8118:8118'
      - '58846:58846'
      - '58946:58946'
    container_name: deluge_hd
    hostname: deluge_hd
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.38
    cap_add:
      - NET_ADMIN
    volumes:
      - 'deluge_hd_data:/data'
      - 'deluge_hd_config:/config'
      - '/etc/localtime:/etc/localtime:ro'
      - '/downloads/hd:/downloads'
    environment:
      - VPN_ENABLED=yes
      - VPN_USER=p2829916
      - VPN_PASS=hA9mRDbEh7
      - VPN_PROV=pia
      - VPN_CLIENT=openvpn
      - STRICT_PORT_FORWARD=yes
      - ENABLE_PRIVOXY=yes
      - LAN_NETWORK=10.0.0.0/24
      - 'NAME_SERVERS=84.200.69.80,37.235.1.174,1.1.1.1,37.235.1.177,84.200.70.40,1.0.0.1'
      - DELUGE_DAEMON_LOG_LEVEL=info
      - DELUGE_WEB_LOG_LEVEL=info
      - VPN_INPUT_PORTS=1234
      - VPN_OUTPUT_PORTS=5678
      - DEBUG=false
      - UMASK=000
      - PUID=0
      - PGID=0
    image: binhex/arch-delugevpn

  deluge_uhd:
    ports:
      - '8112:8112'
      - '8118:8118'
      - '58846:58846'
      - '58946:58946'
    container_name: deluge_uhd
    hostname: deluge_uhd
    networks:
      macvlan_network:
        ipv4_address: 10.0.0.39
    cap_add:
      - NET_ADMIN
    volumes:
      - 'deluge_uhd_data:/data'
      - 'deluge_uhd_config:/config'
      - '/etc/localtime:/etc/localtime:ro'
      - '/downloads/uhd:/downloads'
    environment:
      - VPN_ENABLED=yes
      - VPN_USER=username
      - VPN_PASS=password
      - VPN_PROV=pia
      - VPN_CLIENT=openvpn
      - STRICT_PORT_FORWARD=yes
      - ENABLE_PRIVOXY=yes
      - LAN_NETWORK=10.0.0.0/24
      - 'NAME_SERVERS=84.200.69.80,37.235.1.174,1.1.1.1,37.235.1.177,84.200.70.40,1.0.0.1'
      - DELUGE_DAEMON_LOG_LEVEL=info
      - DELUGE_WEB_LOG_LEVEL=info
      - VPN_INPUT_PORTS=1234
      - VPN_OUTPUT_PORTS=5678
      - DEBUG=false
      - UMASK=000
      - PUID=0
      - PGID=0
    image: binhex/arch-delugevpn

volumes:
  deluge_hd_data:
    external: false
  deluge_hd_config:
    external: false
  deluge_uhd_data:
    external: false
  deluge_uhd_config:
    external: false

networks:
  macvlan_network:
    external:
      name: macvlan_network
```

