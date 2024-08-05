# Portainer Install

``` bash
sudo docker volume create portainer_data
sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

## PORTAINER TEMPLATED

### ORIGINAL

https://raw.githubusercontent.com/portainer/templates/master/templates-2.0.json

### QBALLJOS

https://raw.githubusercontent.com/Qballjos/portainer_templates/master/Template/template.json