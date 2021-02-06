# confluence
default port: 8090

## Requirement
- docker-compose: 17.09.0+

## How to run with docker-compose

- start confluence & mysql

```
    git clone https://github.com/haxqer/confluence.git \
        && cd confluence \
        && docker-compose up
```

- start confluence & mysql daemon

```
    docker-compose up -d
```

- default db(mysql5.7) configure:

```bash
    driver=mysql5.7+
    host=mysql-confluence
    port=3306
    db=confluence
    user=confluence
    passwd=123123
```

## How to run with docker

- start confluence

```
    docker run -p 8090:8090 -v ./confluence:/var/confluence --network confluence-network --name confluence-srv -e TZ='Asia/Shanghai' haxqer/confluence
```

- config your own db:


## How to hack confluence

```
docker exec confluence-srv java -jar /var/agent/atlassian-agent.jar \
    -p conf \
    -m haxqer666@gmail.com \
    -n haxqer666@gmail.com \
    -o http://website \
    -s you-server-id-xxxx
```

## How to hack confluence plugin

- .eg I want to use BigGantt plugin
1. Install BigGantt from confluence marketplace.
2. Find `App Key` of BigGantt is : `eu.softwareplant.biggantt`
3. Execute :

```
docker exec confluence-srv java -jar /var/agent/atlassian-agent.jar \
    -p eu.softwareplant.biggantt \
    -m haxqer666@gmail.com \
    -n haxqer666@gmail.com \
    -o http://website \
    -s you-server-id-xxxx
```

4. Paste your license 

## Install docker & docker-compose
- If you use `debian`, just do it.
```
    ./script/debian-install-docker.sh
    ./script/linux-install-docker-compose.sh
```

## Set Proxy

path : `~/.docker/config.json`

content : 
```
{
    "proxies": {
        "default": {
         "httpProxy": "http://ip:port",
         "httpsProxy": "http://ip:port"
        }
    }
}
```

