# handlpartners-lamp-php56
An Ubuntu-based Docker image for LAMP with PHP 5.6

## Docker Build
docker build -t handlpartners-lamp-php56 .

## Docker Run
docker run -d -P -v /path/to/webroot/folder:/var/www/html handlpartners-lamp-php56

docker ps

## Docker Exec
docker exec -it \<container-id\> /bin/bash

control+p, control+q

## SequelPro Access
1) Visit 127.0.0.1:\<container-http-port\>/adminer.php

2) Login with user root, no pass

3) Set a root password

4) Create a new user {server: %, privs: \*.\*, all privs + grant option}

5) Run the MySQL command 'flush privileges;'

6) Open SequelPro and connect on container port mapped to 3306

