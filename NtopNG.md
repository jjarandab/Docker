# NtopNG Compose

``` yaml
version: '3'

volumes:
  ntopng:
    external: false
  redis:
    external: false

services:

  ntopng:
    image: vimagick/ntopng
    command: --community -d /var/lib/ntopng -i ens160 -r 127.0.0.1:6379@0 -w 0.0.0.0:3000
    volumes:
      - ntopng:/var/lib/ntopng
    network_mode: host
    restart: unless-stopped

  redis:
    image: redis:alpine
    command: --save 900 1
    ports:
      - "6379:6379"
    volumes:
      - redis:/data
    restart: unless-stopped
```

``` bash
sudo firewall-cmd --add-port=3000/tcp
```

