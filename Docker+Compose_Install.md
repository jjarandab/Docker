# Docker+Compose_Install

## UBUNTU

### [Docker Install](https://docs.docker.com/engine/install/ubuntu/)

``` shell
sudo apt-get update
```

``` shell
sudo apt-get install ca-certificates curl gnupg lsb-release -y
```

``` shell
sudo mkdir -p /etc/apt/keyrings
```

``` shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

``` shell
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] [Index of linux/ubuntu/](https://download.docker.com/linux/ubuntu) $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

``` shell
sudo apt-get update
```

``` shell
sudo apt-get install docker-ce docker-ce-cli [containerd.io](http://containerd.io) docker-compose-plugin -y
```

#### [Overlay2 driver](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)

``` shell
sudo systemctl stop docker
```

``` shel
sudo cp -au /var/lib/docker /var/lib/docker.bk
```

``` shell
sudo nano /etc/docker/daemon.json
```

Content:

``` shell
{
"storage-driver": "overlay2"
}
```

``` shell
sudo systemctl start docker
```

``` shell
sudo systemctl enable docker
```



## FEDORA

### [Docker Install](https://docs.docker.com/engine/install/fedora/)

```shell
sudo dnf -y install dnf-plugins-core && sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo && sudo dnf install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

```shell
sudo systemctl start docker && sudo systemctl enable docker.service && sudo systemctl status containerd.service
```

#### [Overlay2 driver](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)

``` shell
sudo systemctl stop docker && cp -au /var/lib/docker /var/lib/docker.bk && yum install nano -y
```

``` shell
nano /etc/docker/daemon.json
```

``` shell
{
"storage-driver": "overlay2"
}
```



## [Compose Install](https://developer.fedoraproject.org/tools/docker/compose.html)

``` shell
sudo dnf install docker-compose -y
```

Notes:

``` shell
10.0.0.32/27
10.0.0.33 - 10.0.0.62
```

