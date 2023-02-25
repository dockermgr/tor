## 👋 Welcome to tor 🚀  

tor README  
  
  
## Requires scripts to be installed  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 systemmgr --config && systemmgr install scripts  
```

## Automatic install/update  

```shell
dockermgr update tor
```

OR

```shell
mkdir -p "$HOME/.local/share/srv/docker/tor/dataDir"
git clone "https://github.com/dockermgr/tor" "$HOME/.local/share/CasjaysDev/dockermgr/tor"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/tor/dataDir/." "$HOME/.local/share/srv/docker/tor/dataDir/"
```

## via command line  

```shell
docker pull casjaysdevdocker/tor:latest && \
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-tor \
--hostname casjaysdev-tor \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/tor/dataDir/data:/data:z \
-v $HOME/.local/share/srv/docker/tor/dataDir/config:/config:z \
-p 80:80 \
casjaysdevdocker/tor:latest
```

## via docker-compose  

```yaml
version: "2"
services:
  tor:
    image: casjaysdevdocker/tor
    container_name: tor
    environment:
      - TZ=America/New_York
      - HOSTNAME=casjaysdev-tor
    volumes:
      - $HOME/.local/share/srv/docker/tor/dataDir/data:/data:z
      - $HOME/.local/share/srv/docker/tor/dataDir/config:/config:z
    ports:
      - 80:80
    restart: always
```

## Author  

📽 dockermgr: [Github](https://github.com/dockermgr) 📽  
🤖 casjay: [Github](https://github.com/casjay) [Docker](https://hub.docker.com/r/casjay) 🤖  
⛵ CasjaysDevDocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/r/casjaysdevdocker) ⛵  
