# DOCKER-WordPress
How to setup WordPress with Docker (Ubuntu 18.04.3 LTS)
https://docs.docker.com

Check if you already have one of this tree elements:
```
$ docker --version
$ docker-compose --version
$ docker-machine --version
```
# 1 Remove older versions
```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

## 1.1 Install DOCKER
`$ sudo apt-get update`
```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
`$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

`$ sudo apt-key fingerprint 0EBFCD88`
<br>Will display  the text below in the console to check the last 8 keys<br>    
```
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```
```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
```
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## 1.2 Test DOCKER
```
$ docker run hello-world
```
This will clone the welcome message from the Docker Hub page and should print :
> `Hello from Docker. This message shows that your installation appears to be working correctly.`

## 1.3 Install DOCKER-MACHINE
```
$ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo mv /tmp/docker-machine /usr/local/bin/docker-machine &&
  chmod +x /usr/local/bin/docker-machine
```
```
$ docker-machine create --driver virtualbox default
```
## 1.4 Install DOCKER-COMPOSE
```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
# 2 DAMP-PMA
**Fork** or **Clone** this [GitHub repo][DampPma] into your local directory (ex. `/home/piralimic/wordpress` ) <br><br>
Now you can **Open in the Terminal** (Ctrl + Alt + T) and follow the last instructions from the [README.md](https://github.com/becodeorg/LIE-Jepsen-2.14/blob/master/02-the-hill/03-wordpress/parcours/docker-compose/README.md) of the linked GitHub repo above.

# 3 HOW-TO solve WordPress PERMALINK error 404
## 3.1 Create new Apache2 .conf with Docker Compose
put `localhost.conf` in the same directory with `docker-compose.yml`<br>
```
$ sudo docker-compose up --build
```
## 3.2 Get access to a bash shell in the container
```
$ sudo docker ps
$ sudo docker exec -i -t nameOfContainer_php-apache_1 /bin/bash
```
## 3.3 Check if 'localhost.conf' is in the right place
```
$ ls /etc/apache2/sites-available/
```
## 3.4 Last step
```
$ a2enmod rewrite
$ service apache2 restart
```
[DampPma]: https://github.com/becodeorg/LIE-Jepsen-2.14/tree/master/02-the-hill/03-wordpress/parcours/docker-compose
