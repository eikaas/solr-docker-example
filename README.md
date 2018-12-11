# solr-docker-psy
### Install docker
```bash
$ /bin/sh <(curl -sSLf https://get.docker.com/)
$ systemctl enable docker
$ systemctl start docker
$ systemctl status docker
```
#### Access the docker daemon as a normal user
(You will need to re-log for this to have an effect)
```bash
$ usermod -aG docker <username>
```

### Clone repository
```bash
$ git clone https://github.com/eikaas/solr-docker-psy
$ cd solr-docker-psy/
```

### Review the .env environment file
```bash
$ cat .env
SOLR_VERSION=7-alpine
SOLR_ADDR=127.0.0.1:8983
SOLR_CORE=mycore
SOLR_DATA_DIR=./data
```

### Start the solr container
* Leave out the `-d` to run it in the foreground
* Consecutive runs of this command updates the container (if any changes are detected)
```
$ docker-compose -f stack.yml up -d
```

### Ensure you can connect to the container
```bash
$ source .env
$ curl -sLI http://${SOLR_ADDR}/solr/ 
HTTP/1.1 200 OK
X-Frame-Options: DENY
Content-Type: text/html;charset=utf-8
Content-Length: 13861
```

### Stop the solr container
```
$ docker-compose -f stack.yml down
```

