Pihole Compose Install

``` yaml
version: "3"

services:
    # Pihole DNS server
    pihole:
      container_name: pihole
      domainname: arandalab.local
      image: pihole/pihole:latest
      hostname: pihole
      networks:
        macvlan_network:
          ipv4_address: 10.0.0.35
      mac_address: d0:ca:ab:cd:ef:05  # Random MAC address (optional)
      ports:
        - '0.0.0.0:53:53/tcp'
        - '0.0.0.0:53:53/udp'
        - '0.0.0.0:67:67/udp'
        - '0.0.0.0:80:80/tcp'
      environment:
        TZ: 'America/Toronto'
        WEBPASSWORD: "050506"
        ServerIP: 10.0.0.35
        VIRTUAL_PORT: 80
      # Volumes store your data between container upgrades
      volumes:
        - pihole:/etc/pihole
        - pihole-dnsmasq:/etc/dnsmasq.d
      dns:
        - 127.0.0.1
        - 1.1.1.1
      cap_add:
        - NET_ADMIN
      restart: unless-stopped

networks:
  macvlan_network:
    external:
      name: macvlan_network

volumes:
  pihole:
  pihole-dnsmasq:
```

