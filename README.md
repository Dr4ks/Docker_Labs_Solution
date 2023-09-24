# Hi, I'm Dr4ks! 👋

## 🚀 About Me
I'm a Cyber Security student.

## 🔗 Links
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/Dr4ks/)
[![hackerrank](https://img.shields.io/badge/HackerRank-2EC866?style=for-the-badge&logo=hackerrank&logoColor=white)](https://www.hackerrank.com/Dr4ks)
[![tryhackme](https://img.shields.io/badge/tryhackme-1DB954?style=for-the-badge&logo=tryhackme&logoColor=white)](https://tryhackme.com/p/Dr4ks)
[![github](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Dr4ks)


## 🛠 Skills
Docker CLI


## Content
- [Introduction](#introduction)
- [Docker Basic](#docker-basics)
- [Docker Run](#docker-run)
- [Docker Images](#docker-images)
- [Docker Envs](#docker-envs)
- [Docker Commands](#docker-commands)
- [Docker Compose](#docker-compose)
- [Docker Storage](#docker-storage)
- [Docker Networking](#docker-networking)


# Introduction
Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and deploy it as one package.

Now, I will answer questions to finish labs from [Docker Labs](https://kodekloud.com/courses/labs-docker-for-the-absolute-beginner-hands-on) on KodeKloud platform.

# Docker Basics
Question:
```bash
What is the version of Docker Server Engine running on the Host?
```

Answer:
```bash
$ docker version
Client: Docker Engine - Community
 Version:           20.10.24
 API version:       1.41
 Go version:        go1.19.7
 Git commit:        297e128
 Built:             Tue Apr  4 18:21:05 2023
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.24
```


Question:
```bash
How many containers are running on this host?
```

Answer:
```bash
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

Question:
```bash
How many images are available on this host?
```

Answer:
```bash
$ docker image ls
REPOSITORY                      TAG       IMAGE ID       CREATED        SIZE
redis                           latest    eca1379fe8b5   5 months ago   117MB
mysql                           latest    8189e588b0e8   5 months ago   564MB
nginx                           latest    6efc10a0510f   5 months ago   142MB
postgres                        latest    ceccf204404e   5 months ago   379MB
nginx                           alpine    8e75cbc5b25c   5 months ago   41MB
alpine                          latest    9ed4aefc74f6   5 months ago   7.04MB
ubuntu                          latest    08d22c0ceb15   6 months ago   77.8MB
kodekloud/simple-webapp-mysql   latest    129dd9f67367   4 years ago    96.6MB
kodekloud/simple-webapp         latest    c6e3cd9aae36   4 years ago    84.8MB
```

Question:
```bash
Run a container using the redis image
```

Answer:
```bash
$ docker run redis
1:C 24 Sep 2023 12:43:53.333 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 24 Sep 2023 12:43:53.333 # Redis version=7.0.11, bits=64, commit=00000000, modified=0, pid=1, just started
1:C 24 Sep 2023 12:43:53.333 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 24 Sep 2023 12:43:53.334 * monotonic clock: POSIX clock_gettime
1:M 24 Sep 2023 12:43:53.338 * Running mode=standalone, port=6379.
1:M 24 Sep 2023 12:43:53.338 # Server initialized
```

Question:
```bash
Stop the container you just created
```

Answer:
```bash
$ docker container stop redis
```

Question:
```bash
How many containers are RUNNING on this host now?
```

Answer:
```bash
$ docker container ls
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS     NAMES
328767d33822   alpine         "sleep 1000"             28 seconds ago   Up 26 seconds             priceless_noether
26a04b0207ab   nginx:alpine   "/docker-entrypoint.…"   30 seconds ago   Up 28 seconds   80/tcp    nginx-2
ad931ecf7142   nginx:alpine   "/docker-entrypoint.…"   33 seconds ago   Up 30 seconds   80/tcp    nginx-1
8b4374345f28   ubuntu         "sleep 1000"             36 seconds ago   Up 32 seconds             awesome_northcut
```


Question:
```bash
How many containers are PRESENT on the host now?


Including both Running and Not Running ones
```

Answer:
```bash
$ docker container ls -a
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                          PORTS     NAMES
829529f8f010   alpine         "/bin/sh"                About a minute ago   Exited (0) About a minute ago             zen_boyd
328767d33822   alpine         "sleep 1000"             About a minute ago   Up About a minute                         priceless_noether
26a04b0207ab   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute               80/tcp    nginx-2
ad931ecf7142   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute               80/tcp    nginx-1
8b4374345f28   ubuntu         "sleep 1000"             About a minute ago   Up About a minute                         awesome_northcut
4db07af9ad0f   redis          "docker-entrypoint.s…"   3 minutes ago        Exited (0) 2 minutes ago                  nervous_haibt
```

Question:
```bash
What is the image used to run the nginx-1 container?
```

Answer:
```bash
$ docker container ls -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                     PORTS     NAMES
829529f8f010   alpine         "/bin/sh"                5 minutes ago   Exited (0) 5 minutes ago             zen_boyd
328767d33822   alpine         "sleep 1000"             5 minutes ago   Up 5 minutes                         priceless_noether
26a04b0207ab   nginx:alpine   "/docker-entrypoint.…"   5 minutes ago   Up 5 minutes               80/tcp    nginx-2
ad931ecf7142  nginx:alpine   "/docker-entrypoint.…"   5 minutes ago   Up 5 minutes               80/tcp     nginx-1
8b4374345f28   ubuntu         "sleep 1000"             5 minutes ago   Up 5 minutes                         awesome_northcut
4db07af9ad0f   redis          "docker-entrypoint.s…"   7 minutes ago   Exited (0) 6 minutes ago             nervous_haibt
```

Question:
```bash
What is the name of the container created using the ubuntu image?
```

Answer:
```bash   
$ docker container ls -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                     PORTS     NAMES
829529f8f010   alpine         "/bin/sh"                5 minutes ago   Exited (0) 5 minutes ago             zen_boyd
328767d33822   alpine         "sleep 1000"             5 minutes ago   Up 5 minutes                         priceless_noether
26a04b0207ab   nginx:alpine   "/docker-entrypoint.…"   6 minutes ago   Up 5 minutes               80/tcp    nginx-2
ad931ecf7142   nginx:alpine   "/docker-entrypoint.…"   6 minutes ago   Up 6 minutes               80/tcp    nginx-1
8b4374345f28   ubuntu         "sleep 1000"             6 minutes ago   Up 6 minutes                         awesome_northcut
4db07af9ad0f   redis          "docker-entrypoint.s…"   8 minutes ago   Exited (0) 7 minutes ago             nervous_haibt
```

Question:
```bash
What is the ID of the container that uses the alpine image and is not running?
```

Answer:
```bash
$ docker container ls -a | grep 'alpine' | grep 'Exited'
829529f8f010   alpine         "/bin/sh"                8 minutes ago    Exited (0) 8 minutes ago             zen_boyd
```

Question:
```bash
Delete all containers from the Docker Host.

Both Running and Not Running ones. Remember you may have to stop containers before deleting them.
```

Answer:
```bash
$ docker ps -aq
829529f8f010
328767d33822
26a04b0207ab
ad931ecf7142
8b4374345f28
4db07af9ad0f

Then, start removing
$ docker rm $(docker ps -aq) --force
328767d33822
26a04b0207ab
ad931ecf7142
8b4374345f28
```

Question:
```bash
Delete the ubuntu Image.
```

Answer:
```bash
$ docker image rm ubuntu
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:67211c14fa74f070d27cc59d69a7fa9aeff8e28ea118ef3babc295a0428a6d21
Deleted: sha256:08d22c0ceb150ddeb2237c5fa3129c0183f3cc6f5eeb2e7aa4016da3ad02140a
Deleted: sha256:b93c1bd012ab8fda60f5b4f5906bf244586e0e3292d84571d3abb56472248466
```

Question:
```bash
You are required to pull a docker image which will be used to run a container later. Pull the image nginx:1.14-alpine


Only pull the image, do not create a container.
```

Answer:
```bash
$ docker pull nginx:1.14-alpine
1.14-alpine: Pulling from library/nginx
bdf0201b3a05: Pull complete 
3d0a573c81ed: Pull complete 
8129faeb2eb6: Pull complete 
3dc99f571daf: Pull complete 
Digest: sha256:485b610fefec7ff6c463ced9623314a04ed67e3945b9c08d7e53a47f6d108dc7
Status: Downloaded newer image for nginx:1.14-alpine
docker.io/library/nginx:1.14-alpine
```

Question:
```bash
Run a container with the nginx:1.14-alpine image and name it webapp
```

Answer:
```bash
$ docker run -d --name webapp nginx:1.14-alpine
b6e0ced33b70b8e8e93f2cc4ec1b4e1c40c43d6a57ceb563d0d6572c4b233203
```

Question:
```bash
Cleanup: Delete all images on the host


Remove containers as necessary
```

Answer:
```bash
$ docker image ls -aq    #to see all container images
eca1379fe8b5
8189e588b0e8
6efc10a0510f
ceccf204404e
8e75cbc5b25c
9ed4aefc74f6
8a2fb25a19f5
129dd9f67367
c6e3cd9aae36

$ docker image rm $(docker image ls -aq) --force   #to delete all container images
```

# Docker Run

Question:
```bash
Let us first inspect the environment. How many containers are running on this host?
```

Answer:
```bash
$ docker container ls
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                           NAMES
d5259591611a   nginx:alpine   "/docker-entrypoint.…"   26 seconds ago   Up 24 seconds   0.0.0.0:3456->3456/tcp, 0.0.0.0:38080->80/tcp   vigorous_keller
```


Question:
```bash
What is the image used by the container?
```

Answer:
```bash
$ docker container ls
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                           NAMES
d5259591611a   nginx:alpine   "/docker-entrypoint.…"   26 seconds ago   Up 24 seconds   0.0.0.0:3456->3456/tcp, 0.0.0.0:38080->80/tcp   vigorous_keller
```


Question:
```bash
How many ports are published on this container?
```

Answer:
```bash
$ docker inspect $(docker container ls -aq)
"Ports": {
                "3456/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "3456"
                    }
                ],
                "80/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "38080"
                    }
                ]
            },
```


Question:
```bash
Run an instance of kodekloud/simple-webapp with a tag blue and map port 8080 on the container to 38282 on the host.
```

Answer:
```bash
$ docker run -d -p 38282:8080 kodekloud/simple-webapp:blue
Unable to find image 'kodekloud/simple-webapp:blue' locally
blue: Pulling from kodekloud/simple-webapp
4fe2ade4980c: Already exists 
7cf6a1d62200: Already exists 
f0d690b9e495: Already exists 
fac5d45ad062: Already exists 
a6fc8a0deb7d: Pull complete 
f43c8e496f88: Pull complete 
58ca939f7651: Pull complete 
095a1a007cdb: Pull complete 
Digest: sha256:9caf15476dc60b77c7460791bea8ea5f6ca02b90199aabe088beea83bc943fe5
Status: Downloaded newer image for kodekloud/simple-webapp:blue
a9707f4ce8e31553d2f7c99436a155b33b18e83d92f92ff2bf95905d2e9ff0e9
```


# Docker Images

Question:
```bash
How many images are available on this host?
```

Answer:
```bash
$ docker image ls
REPOSITORY                      TAG       IMAGE ID       CREATED        SIZE
redis                           latest    eca1379fe8b5   5 months ago   117MB
mysql                           latest    8189e588b0e8   5 months ago   564MB
nginx                           latest    6efc10a0510f   5 months ago   142MB
postgres                        latest    ceccf204404e   5 months ago   379MB
nginx                           alpine    8e75cbc5b25c   5 months ago   41MB
alpine                          latest    9ed4aefc74f6   5 months ago   7.04MB
ubuntu                          latest    08d22c0ceb15   6 months ago   77.8MB
kodekloud/simple-webapp-mysql   latest    129dd9f67367   4 years ago    96.6MB
kodekloud/simple-webapp         latest    c6e3cd9aae36   4 years ago    84.8MB
```

Question:
```bash
How many images are available on this host?
```

Answer:
```bash
$ docker image ls
REPOSITORY                      TAG       IMAGE ID       CREATED        SIZE
ubuntu                          latest    08d22c0ceb15   6 months ago   77.8MB
```

Question:
```bash
We just pulled a new image. What is the tag on the newly pulled NGINX image?
```

Answer:
```bash
$ docker image ls
REPOSITORY                      TAG           IMAGE ID       CREATED        SIZE
nginx                           1.14-alpine   8a2fb25a19f5   4 years ago    16MB
```

Question:
```bash
We just downloaded the code of an application. What is the base image used in the Dockerfile?


Inspect the Dockerfile in the webapp-color directory.
```

Answer:
```bash
$ cat webapp-color/Dockerfile 
FROM python:3.6

RUN pip install flask

COPY . /opt/

EXPOSE 8080

WORKDIR /opt

ENTRYPOINT ["python", "app.py"]
```

Question:
```bash
When a container is created using the image built with this Dockerfile, what is the command used to RUN the application inside it.


Inspect the Dockerfile in the webapp-color directory.
```

Answer:
```bash
$ cat webapp-color/Dockerfile 
FROM python:3.6

RUN pip install flask

COPY . /opt/

EXPOSE 8080

WORKDIR /opt

ENTRYPOINT ["python", "app.py"]
```


Question:
```bash
What port is the web application run within the container?


Inspect the Dockerfile in the webapp-color directory.
```


Answer:
```bash
$ cat webapp-color/Dockerfile 
FROM python:3.6

RUN pip install flask

COPY . /opt/

EXPOSE 8080

WORKDIR /opt

ENTRYPOINT ["python", "app.py"]
```


Question:
```bash
Build a docker image using the Dockerfile and name it webapp-color. No tag to be specified.
```

Answer:
```bash
$ docker build -t webapp-color webapp-color
```


Question:
```bash
Run an instance of the image webapp-color and publish port 8080 on the container to 8282 on the host.
```

Answer:
```bash
$ docker container run -d -p 8282:8080 webapp-color
e9bf9501626e9542b5839af930fb5b7441b537b1cdc727f2f7598c4cc87e065b
```


Question:
```bash
What is the approximate size of the webapp-color image?
```

Answer:
```bash
$ docker image ls | grep "webapp-color"
webapp-color                    latest        e742f4d8648f   6 minutes ago   913MB
```


Question:
```bash
Build a new smaller docker image by modifying the same Dockerfile and name it webapp-color and tag it lite.


Hint: Find a smaller base image for python:3.6. Make sure the final image is less than 150MB.
```

Answer: 
```bash
$ cat Dockerfile   #first change python to python:3.6-alpine
FROM python:3.6-alpine

RUN pip install flask

COPY . /opt/

EXPOSE 8080

WORKDIR /opt

ENTRYPOINT ["python", "app.py"]

$ docker build -t webapp-color:lite .
```


Question:
```bash
Run an instance of the new image webapp-color:lite and publish port 8080 on the container to 8383 on the host.
```

Answer:
```bash
$ docker container run -d -p 8383:8080 webapp-color:lite
52464d475fce40cf6bf972331643e3a065d587f57bbcb8497e688435f520d801
```

# Docker Envs

Question:
```bash
Inspect the environment variables set on the running container and identify the value set to the APP_COLOR variable.
```

Answer:
```bash
$ docker container ls
CONTAINER ID   IMAGE                     COMMAND           CREATED          STATUS          PORTS      NAMES
0985f8303d49   kodekloud/simple-webapp   "python app.py"   14 seconds ago   Up 13 seconds   8080/tcp   epic_panini
$ docker inspect 0985f8303d49
            "Env": [
                "APP_COLOR=pink",
                "PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LANG=C.UTF-8",
                "GPG_KEY=0D96DF4D4110E5C43FBFB17F2D347EA6AA65421D",
                "PYTHON_VERSION=3.6.6",
                "PYTHON_PIP_VERSION=18.1"
            ],
```


Question:
```bash
Run a container named blue-app using image kodekloud/simple-webapp and set the environment variable APP_COLOR to blue. Make the application available on port 38282 on the host. The application listens on port 8080.
```

Answer:
```bash
$ docker container run -d -p 38282:8080 --name blue-app -e APP_COLOR=blue kodekloud/simple-webapp
909e0479992e0c2572aabefde7a2c617c4bccb5f766b592f627598bb6f5d203c
```


Question:
```bash
Deploy a mysql database using the mysql image and name it mysql-db.


Set the database password to use db_pass123. Lookup the mysql image on Docker Hub and identify the correct environment variable to use for setting the root password.
```

Answer:
```bash
$ docker container run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql
d46c3ef826477c53c1dd101aaf063997596dbedab79759b152f026518f8d9023
```

# Docker Commands

Question:
```bash
What is the ENTRYPOINT configured on the mysql image?
```

Answer:
```bash
$ cat Dockerfile-mysql | grep "ENTRYPOINT"
ENTRYPOINT ["docker-entrypoint.sh"]
```

Question:
```bash
What is the CMD configured on the wordpress image?
```

Answer:
```bash
$ cat Dockerfile-wordpress | grep "CMD"
CMD ["apache2-foreground"]
```

Question:
```bash
What is the final command run at startup when the wordpress image is run. Consider both ENTRYPOINT and CMD instructions
```

Answer:
```bash
$ cat Dockerfile-wordpress | grep "CMD"
CMD ["apache2-foreground"]
$ cat Dockerfile-wordpress | grep "ENTRYPOINT"
ENTRYPOINT ["docker-entrypoint.sh"]
```


Question:
```bash
What is the command run at startup when the ubuntu image is run?
```

Answer:
```bash
$ cat Dockerfile-ubuntu | grep "CMD"
CMD ["bash"]
```


Question:
```bash
Run an instance of the ubuntu image to run the sleep 1000 command at startup.


Run it in detached mode.
```

Answer:
```bash
$ docker container run -d --name ubuntu-sleeper ubuntu sleep 1000
78dbf2c180aa5e9c0e4ba96b3e26cbf5c6a30fd48d1a501b775f10905d06ff29
```

# Docker Compose

Question:
```bash
First create a redis database container called redis, image redis:alpine.


if you are unsure, check the hints section for the exact commands.
```

Answer:
```bash
$ docker container run -d --name redis redis:alpine
Unable to find image 'redis:alpine' locally
alpine: Pulling from library/redis
7264a8db6415: Pull complete 
a28817da73be: Pull complete 
536ccaebaffb: Pull complete 
cf393c8f1348: Pull complete 
e450001ba352: Pull complete 
e704b26e22f6: Pull complete 
Digest: sha256:ef3296cb1b3a7eb40f2a992a398777a1c0b5b21df44f1a5bef84067f772daf54
Status: Downloaded newer image for redis:alpine
5fb03179f382ca6b4be74979fbbc21e6d9d9a81b91a2bb9c90b93fa5845fdea9
```


Question:
```bash
Next, create a simple container called clickcounter with the image kodekloud/click-counter, link it to the redis container that we created in the previous task and then expose it on the host port 8085


The clickcounter app run on port 5000.
if you are unsure, check the hints section for the exact commands.
```

Answer:
```bash
$ docker container run -d --name clickcounter --link redis -p 8085:5000 kodekloud/click-counter
Unable to find image 'kodekloud/click-counter:latest' locally
latest: Pulling from kodekloud/click-counter
540db60ca938: Pull complete 
a7ad1a75a999: Pull complete 
37ce6546d5dd: Pull complete 
ec9e91bed5a2: Pull complete 
767433e10bb0: Pull complete 
156f0b0493cb: Pull complete 
3fe82d8a2401: Pull complete 
4a41f7c94204: Pull complete 
473063430a4f: Pull complete 
452c68a16ccd: Pull complete 
Digest: sha256:530e4532a718e8f5cbda05844a6c0638ebe8898fa4c4307ee6afbdd5d1f213db
Status: Downloaded newer image for kodekloud/click-counter:latest
0d43e082c6dd996ade594ca34d639e48288c3c1dc962c418dbff97e32adeca24
```

Question:
```bash
Let's clean up the actions carried out in previous steps. Delete the redis and the clickcounter containers.
```

Answer:
```bash
$ docker container ls -aq
0d43e082c6dd
5fb03179f382
$ docker container rm $(docker container ls -aq) --force
0d43e082c6dd
5fb03179f382
```

Question:
```bash
Create a docker-compose.yml file under the directory /root/clickcounter. Once done, run docker-compose up.


The compose file should have the exact specification as follows -

redis service specification - Image name should be redis:alpine.
clickcounter service specification - Image name should be kodekloud/click-counter, app is run on port 5000 and expose it on the host port 8085 in the compose file.
```

Answer:
```bash  
$ cd /root/clickcounter  # we change directory to /root/clickcounter
$ pwd
/root/clickcounter

$ touch docker-compose.yml  # we create docker-compose.yml file
$ ls
docker-compose.yml

$ vim docker-compose.yml   # we edit docker-compose.yml file
$ cat docker-compose.yml 
version: '3.8'

services:
  redis:
    image: redis:alpine

  clickcounter:
    image: kodekloud/click-counter
    ports:
      - '8085:5000'


$ docker-compose up
```

# Docker Storage

Question:
```bash
What location are the files related to the docker containers and images stored?
```

Answer:
```bash
$ docker info | grep "Docker Root Dir"
Docker Root Dir: /var/lib/docker
```

Question:
```bash
What directory under /var/lib/docker are the files related to the container alpine-3 image stored?
```

Answer:
```bash
$ docker inspect alpine-3 | grep "Id"
        "Id": "48a7de550f6268d17c818745496fd1b92a9f3093371a096ded04997b7cc4dcbd",
```


Question:
```bash
Run a mysql container named mysql-db using the mysql image. Set database password to db_pass123


Note: Remember to run it in the detached mode.
```

Answer:
```bash
$ docker container run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 mysql
6ddc029815318be19ff41fdbb1521c9a9d0980e71556428ebf8245915800b3d0
```

Question:
```bash
We have just written some data into the database. To view the information we wrote, run the get-data.sh bash available in the /root directory. How many customers data have been written to the database?


Command: sh get-data.sh
```

Answer:
```bash
$ sh get-data.sh
```

**AFTER CRASHING MYSQL DB , WE UNDERSTOOD THAT WE NEED TO ADD VOLUME TO SAVE DATA**

Question:
```bash
Run a mysql container again, but this time map a volume to the container so that the data stored by the container is stored at /opt/data on the host.


Use the same name : mysql-db and same password: db_pass123 as before. Mysql stores data at /var/lib/mysql inside the container.
```

Answer:
```bash
$ docker container run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 -v /opt/data:/var/lib/mysql mysql
79791c6d80eae988dbf0775d462373eaa822a2072b05f7ea8e8ce9cc9189f327
```

# Docker Networking

Question:
```bash
Explore the current setup and identify the number of networks that exist on this system.
```

Answer:
```bash
$ docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
5b1e25ce69bc   bridge    bridge    local
e1bd4eeb89ea   host      host      local
cc017d20d8c9   none      null      local
```

Question:
```bash
What is the ID associated with the bridge network?
```

Answer:
```bash
$ docker network ls | grep "bridge"
5b1e25ce69bc   bridge    bridge    local
```

Question:
```bash
We just ran a container named alpine-1. Identify the network it is attached to.
```

Answer:
```bash
$ docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
5b1e25ce69bc   bridge    bridge    local
e1bd4eeb89ea   host      host      local
cc017d20d8c9   none      null      local

$ docker inspect alpine-1 | grep "NetworkID"   # we understand that alpine-1 is attached to host network
                    "NetworkID": "e1bd4eeb89ea00d56f811c10a01bc5a672bcf1487b483acee53a406886b29b21",
```

Question:
```bash
What is the subnet configured on bridge network?
```

Answer:
```bash
$ docker network inspect bridge | grep "Subnet"
                    "Subnet": "172.12.0.0/24",
```


Question:
```bash
Run a container named alpine-2 using the alpine image and attach it to the none network.
```

Answer:
```bash
$ docker container run -d --name alpine-2 --network none alpine
dd6691d699b95c2b1ca051f20f3f18b8352551b9ffef63902c687dd77791bcbc
```


Question:
```bash
Create a new network named wp-mysql-network using the bridge driver. Allocate subnet 182.18.0.1/24. Configure Gateway 182.18.0.1
```

Answer:
```bash
$ docker network create --driver bridge --subnet 182.18.0.1/24 --gateway 182.18.0.1 wp-mysql-network
a6a6574721bfd925fc773ffb7f73b5f2a2588ec713e8d282e5d0962687be87e5
```


Question:
```bash
Deploy a mysql database using the mysql:5.6 image and name it mysql-db. Attach it to the newly created network wp-mysql-network


Set the database password to use db_pass123. The environment variable to set is MYSQL_ROOT_PASSWORD.
```

Answer:
```bash
$ docker container run -d --name mysql-db -e MYSQL_ROOT_PASSWORD=db_pass123 --network wp-mysql-network mysql:5.6
Unable to find image 'mysql:5.6' locally
5.6: Pulling from library/mysql
35b2232c987e: Pull complete 
fc55c00e48f2: Pull complete 
0030405130e3: Pull complete 
e1fef7f6a8d1: Pull complete 
1c76272398bb: Pull complete 
f57e698171b6: Pull complete 
f5b825b269c0: Pull complete 
dcb0af686073: Pull complete 
27bbfeb886d1: Pull complete 
6f70cc868145: Pull complete 
1f6637f4600d: Pull complete 
Digest: sha256:20575ecebe6216036d25dab5903808211f1e9ba63dc7825ac20cb975e34cfcae
Status: Downloaded newer image for mysql:5.6
6e7a55afd542f8470303dc30ba91d6b11544911322e51f43ca10bdfcdc585f68
```


Question:
```bash
Deploy a web application named webapp using the kodekloud/simple-webapp-mysql image. Expose the port to 38080 on the host.

The application makes use of two environment variable:
1: DB_Host with the value mysql-db.
2: DB_Password with the value db_pass123.
Make sure to attach it to the newly created network called wp-mysql-network.


Also make sure to link the MySQL and the webapp container.
```


Answer:
```bash
$ docker container run -d --name webapp -e DB_Host=mysql-db -e DB_Password=db_pass123 --network wp-mysql-network -p 38080 kodekloud/simple-webapp-mysql
5d6d011373c376944f313d768296c806397a84176be982f61834b1c40a24f88d
```


## Authors
- [@dr4ks](https://www.github.com/Dr4ks)