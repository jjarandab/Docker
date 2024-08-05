# Docker+Compose_Install

## UBUNTU

### [Docker Install](https://docs.docker.com/engine/install/ubuntu/)

- sudo apt-get update
- sudo apt-get install ca-certificates curl gnupg lsb-release -y
- sudo mkdir -p /etc/apt/keyrings
- curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
- echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] [Index of linux/ubuntu/](https://download.docker.com/linux/ubuntu) $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
- sudo apt-get update
- sudo apt-get install docker-ce docker-ce-cli [containerd.io](http://containerd.io) docker-compose-plugin -y



#### [Overlay2 driver](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)

- sudo systemctl stop docker
- sudo cp -au /var/lib/docker /var/lib/docker.bk
- sudo nano /etc/docker/daemon.json

{   "storage-driver": "overlay2" }

- sudo systemctl start docker
- sudo systemctl enable docker



## FEDORA

### [Docker Install](https://docs.docker.com/engine/install/fedora/)

`sudo dnf -y install dnf-plugins-core && sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo && sudo dnf install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y`

`sudo systemctl start docker && sudo systemctl enable docker.service && sudo systemctl status containerd.service`



#### [Overlay2 driver](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)

- ``` sudo systemctl stop docker && cp -au /var/lib/docker /var/lib/docker.bk && yum install nano -y
- `nano /etc/docker/daemon.json`

`{

"storage-driver": "overlay2"

}`



## [Compose Install](https://developer.fedoraproject.org/tools/docker/compose.html)

`sudo dnf install docker-compose -y`

10.0.0.32/27

10.0.0.33 - 10.0.0.62


