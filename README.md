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
- [Docker Registry](#docker-registry)


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

- # Docker Registry

Question:
```bash
What is a Docker Registry?
```

Answer:
```bash
It is a storage and distribution system for name Docker images
```

Question:
```bash
By default, the Docker engine interacts with ?
```

Answer:
```bash
DockerHub
```

Question:
```bash
Which command is used for Login to a self-hosted registry?
```

Answer:
```bash
docker login [SERVER]
```

Question:
```bash
Let practice deploying a registry server on our own.
Run a registry server with name equals to my-registry using registry:2 image with host port set to 5000, and restart policy set to always.

Note: Registry server is exposed on port 5000 in the image.

Here we are hosting our own registry using the open source Docker Registry.
```

Answer:
```bash
$ docker run -d --name my-registry -p 5000:5000 --restart always registry:2
```

Question:
```bash
Now its time to push some images to our registry server. Let's push two images for now .i.e. nginx:latest and httpd:latest.

Note: Don't forget to pull them first.

To check the list of images pushed , use curl -X GET localhost:5000/v2/_catalog
```

Answer:
```bash
$ docker pull nginx:latest
latest: Pulling from library/nginx
f11c1adaa26e: Pull complete 
c6b156574604: Pull complete 
ea5d7144c337: Pull complete 
1bbcb9df2c93: Pull complete 
537a6cfe3404: Pull complete 
767bff2cc03e: Pull complete 
adc73cb74f25: Pull complete 
Digest: sha256:67682bda769fae1ccf5183192b8daf37b64cae99c6c3302650f6f8bf5f0f95df
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
$ docker image tag nginx:latest localhost:5000/nginx:latest
$ docker push localhost:5000/nginx:latest
The push refers to repository [localhost:5000/nginx]
56b6d3be75f9: Pushed 
0c6c257920c8: Pushed 
92d0d4e97019: Pushed 
7190c87a0e8a: Pushed 
933a3ce2c78a: Pushed 
32cfaf91376f: Pushed 
32148f9f6c5a: Pushed 
latest: digest: sha256:c94f3436f3bfcb467e9723bdb4957e2e86c00cc5f21e38a40d668c1a4c324696 size: 1778

$ curl -X GET localhost:5000/v2/_catalog
{"repositories":["nginx"]}

$ docker pull httpd:latest
latest: Pulling from library/httpd
f11c1adaa26e: Already exists 
48478b514cc0: Pull complete 
4f4fb700ef54: Pull complete 
b8b3bb7c6a0f: Pull complete 
9060cfd4884f: Pull complete 
53a62d5d4966: Pull complete 
Digest: sha256:9738e4f0bfa4b0e5d78318ad858ec04747d98f60afccf9f7757362e948d3990c
Status: Downloaded newer image for httpd:latest
docker.io/library/httpd:latest
$ docker image tag httpd:latest localhost:5000/httpd:latest
$ docker push localhost:5000/httpd:latest
The push refers to repository [localhost:5000/httpd]
16bbf79a16f0: Pushed 
842c1a14d08e: Pushed 
07a2e7c7a125: Pushed 
5f70bf18a086: Pushed 
276b52f72ad3: Pushed 
32148f9f6c5a: Mounted from nginx 
latest: digest: sha256:07776427935a87ffaaca2875af6b19441e08ca4c7a18dafaf9ac9a7ff38dfe9e size: 1572
$ curl -X GET localhost:5000/v2/_catalog
{"repositories":["httpd","nginx"]}
```

Question:
```bash
Let's remove all the dangling images we have locally. Use docker image prune -a to remove them. How many images do we have now?

Note: Make sure we don't have any running containers except our registry-sever.

To get list of images use: docker image ls
```

Answer:
```bash
$ docker ps
CONTAINER ID   IMAGE        COMMAND                  CREATED         STATUS         PORTS                    NAMES
699adcdf5d8e   registry:2   "/entrypoint.sh /etc…"   8 minutes ago   Up 8 minutes   0.0.0.0:5000->5000/tcp   my-registry
$ docker stop my-registry
my-registry
$ docker image prune -a
WARNING! This will remove all images without at least one container associated to them.
Are you sure you want to continue? [y/N] y
Deleted Images:
untagged: kodekloud/simple-webapp-mysql:latest
untagged: kodekloud/simple-webapp-mysql@sha256:92943d2b3ea4a1db7c8a9529cd5786ae3b9999e0246ab665c29922e9800d1b41
deleted: sha256:129dd9f673673e9e8507ac837dcd9eaa3906469c10ef4aa63d0cac1f1dfa6b3a
deleted: sha256:07711c2005c750fa9c42f5667ec657d7f5126f710915cf917cf5c0e9e3871242
deleted: sha256:69dbe0a61b055e5e63706bc76a875220e02769e880d1846c6f965c2f4b1b1dfe
deleted: sha256:5978a6831cce81b23e657b11150010eb8acf463a183cbe540eb6c769314a0f8a
deleted: sha256:93099f51e789a3d87e77501591ab260ca2ff9b8532a78f9fc6bebaa2d5ffcad4
deleted: sha256:15df614f20bc13c6da75c43616dec28d17908970491a562820fabbc11a1e562c
deleted: sha256:a8dc474c5cce41198ea9a334a54bd7d59043f86c32c3b8e3f0d76a52adf09cf2
deleted: sha256:362e5432c5954e9f081657f369b00d821cecd10274b8885f1d6fd1b2e8c1a405
deleted: sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c
untagged: httpd:latest
untagged: httpd@sha256:9738e4f0bfa4b0e5d78318ad858ec04747d98f60afccf9f7757362e948d3990c
untagged: localhost:5000/httpd:latest
untagged: localhost:5000/httpd@sha256:07776427935a87ffaaca2875af6b19441e08ca4c7a18dafaf9ac9a7ff38dfe9e
deleted: sha256:b21577b6946fec9df0eaa3c21748d361bc19742ddb6185a4201baa4200fb35fa
deleted: sha256:bdc77642641dda5c134e9fc1cac146926122c7886eea3e559d0395c997a104ea
deleted: sha256:e2a8ba32b61fe74a83dc3d9738b2e44f3274dcc844cb082b730fe086a0e6527f
deleted: sha256:e1fe6e8d4cfe042147e67cc073939cabbfdd04e0f5b5c95a74156e45ad0eeb3c
deleted: sha256:805bfaf73fda03633d99574b54d4cf34fdabbceddad5ec6aee5d3de007a94853
deleted: sha256:802821aca9256bdf317b8131582df1830432e4d46b95400011f0629e5942faf6
untagged: redis:latest
untagged: redis@sha256:f50031a49f41e493087fb95f96fdb3523bb25dcf6a3f0b07c588ad3cdbe1d0aa
deleted: sha256:eca1379fe8b541831fd5ce4a252c263db0cef4efbfd428a94225dc020aaeb1af
deleted: sha256:21acda8c08f1a6109e2fb61ed010d368ee6581cf30128cdaab0e6b91dabffc22
deleted: sha256:aafc83c9f9299ba7a3af08ab0b1f822340278803714695fd2a96351fe89b37ea
deleted: sha256:644ab96acc6e4232dc7be6f1855b27f5f3534b17b9e9c19ae2557991b99487db
deleted: sha256:6e75f4867056adfca8dfafbb0e94a525064797e4f0a106bca817b5afce47af73
deleted: sha256:84e4c46eefa83bc327e4e356365ec03a3ee1f691d181235e5b69e36663f7dd57
untagged: ubuntu:latest
untagged: ubuntu@sha256:67211c14fa74f070d27cc59d69a7fa9aeff8e28ea118ef3babc295a0428a6d21
deleted: sha256:08d22c0ceb150ddeb2237c5fa3129c0183f3cc6f5eeb2e7aa4016da3ad02140a
deleted: sha256:b93c1bd012ab8fda60f5b4f5906bf244586e0e3292d84571d3abb56472248466
untagged: nginx:latest
untagged: nginx@sha256:67682bda769fae1ccf5183192b8daf37b64cae99c6c3302650f6f8bf5f0f95df
untagged: localhost:5000/nginx:latest
untagged: localhost:5000/nginx@sha256:c94f3436f3bfcb467e9723bdb4957e2e86c00cc5f21e38a40d668c1a4c324696
deleted: sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765c
deleted: sha256:9f4b5d44149fd139616539e0ef5311a14338a970f25733ba95b4ae6d3becdf0d
deleted: sha256:8e6e10fbcca1bb180c5cfc805a37240945a6ba703cb1f985d4d3b8a1c954fc5b
deleted: sha256:dcec89b921d64a1d2f748c450832a4c5624219bbb1b696e1a606bff78b7afa60
deleted: sha256:4994a8d5939af297abf594b7ab714dfb72e57217b94bf0a250a62903cbdb6d84
deleted: sha256:8b2bc37f672b15bea06a204790da9f384ef7b06feccade3fd3b1945b63df5aef
deleted: sha256:a4197512070a01764db77b424100c1f81f0ed696380b19bc26b6e72fafef0709
deleted: sha256:32148f9f6c5aadfa167ee7b146b9703c59307049d68b090c19db019fd15c5406
untagged: mysql:latest
untagged: mysql@sha256:a43f6e7e7f3a5e5b90f857fbed4e3103ece771b19f0f75880f767cf66bbb6577
deleted: sha256:8189e588b0e8fcc95b0d764d6f7bdb55b5b41e9249157177d73781058f603ca9
deleted: sha256:48c450c06ed83938e899fb0b77b2e9e35094015b503bb5e88de6c2d93f445241
deleted: sha256:c5d77efb49ec3a7a74ab898b9da9217ec78fa9bee47018409025467611d60329
deleted: sha256:de0c00e28b37cc33347f02709e0a6a2f17637b1e761fb96616861ed345bd34f6
deleted: sha256:cc635684e233946f93fe008e0322c86e15cbb97b56c58d269a5f8f9da15d973d
deleted: sha256:0b795b85d567512d79a544b1b74f21108339156cbbc78d16921e96a2a69f687b
deleted: sha256:16e250c36f4c0e1085512653edd47fd03b60d230ddb575aabc8eb224d96e668f
deleted: sha256:d023b92a46a5fa8fa8d54387e6d3cb0c73997fefc64ec9000eab0ee1c550ef45
deleted: sha256:f1c1643119168a94089eab1c9126cda0ee6056a4bb4b18e27a7dcacdf4823972
deleted: sha256:b147319dd21e8994e6d2fb3bb58a8278c5a72f39488e1f1cff94fc73f1089eb9
deleted: sha256:ff7c2b28c0dfaa63d0d30b7a5069bf526b0f6492143110381351bbf7d07b4baf
deleted: sha256:caefa4e45110eab274ebbdbc781f9227229f947f8718cee62ebeff1aac8f1d5b
untagged: alpine:latest
untagged: alpine@sha256:124c7d2707904eea7431fffe91522a01e5a861a624ee31d03372cc1d138a3126
deleted: sha256:9ed4aefc74f6792b5a804d1d146fe4b4a2299147b0f50eaf2b08435d7b38c27e
deleted: sha256:f1417ff83b319fbdae6dd9cd6d8c9c88002dcd75ecf6ec201c8c6894681cf2b5
untagged: postgres:latest
untagged: postgres@sha256:6cc97262444f1c45171081bc5a1d4c28b883ea46a6e0d1a45a8eac4a7f4767ab
deleted: sha256:ceccf204404e5efe764f2d4d97e6977db04062579d525d9cb445cf93e0f0fef4
deleted: sha256:5581e2a0252cdb4f2b1847cfd9300122841787cd0a9ba13e095425b22c08bb05
deleted: sha256:b8d9a959ce0f6039bf4061ddedb320c05b9b049b5bd8dabb2b5f9d697fdc4e0e
deleted: sha256:d426781ae8413908a52d86fb8f28319b834625c5c6b194e3d122d1b1eb179d87
deleted: sha256:ee6f16055bfd3ad8bcc92a9af3567c69c0bb499cbc2c2b9a2f2ccafa3538504b
deleted: sha256:42c973890245849bff76e03def91ceacb87da92a19fa5aa7eab58975a811c683
deleted: sha256:179015cc5c69fea24583ca7a52a8ba75dd363310d17461b6eb9b430c0d69a37e
deleted: sha256:9362c3f758a9916eb7e2262af8e63d7f1b0a45818e7ac033c9152ecf049933d0
deleted: sha256:b47ed6c8bc9fa1548ed586316aa7a0e27b34937efb1b3c4ad5742ae3a5d63f8c
deleted: sha256:a603ddfeb1e19bb984a56b96e96cc987d8e27621390a9bc1b11f7003ff357e7d
deleted: sha256:ca073f3da5fc959ed40fff93ae9a550ddb14916b3f8bd620235d306f5e9d3d64
deleted: sha256:fd2d7bb88deba0351caf0ee032dac84272a04e489fd055407cddd740009e329c
deleted: sha256:2c3cc0e91a94c04e5446f3a8061970073053850ce8093a46ba819b8e59af1dee
deleted: sha256:ed7b0ef3bf5bbec74379c3ae3d5339e666a314223e863c70644f7522a7527461
untagged: kodekloud/simple-webapp:latest
untagged: kodekloud/simple-webapp@sha256:e5355b4c7804f453d79de75d6659ee702eeebbe30c02d9f1ce6602a96b576e57
deleted: sha256:c6e3cd9aae3645a98dd69c15b048614603efce6cda26c60f5f7e867ef68f729f
deleted: sha256:33833b97952fc68d999bc3bccaad23687ea6a939724e0130c151dc973ba8f2d3
deleted: sha256:a3dd002bb33a1cdb83aface983ea0d268be1b4ffda0e42ce72aa5c22ced6701f
deleted: sha256:12e8c893d121075ced84d32b967f6de75ff67e1cf7c9b66b63636bdf630ac12c
deleted: sha256:4785d1dd03a24d6b30c9342db24ac2254d01362e7f3b3f28f55a00e4858f85e5
deleted: sha256:9de207c08e3d729c3b9c451d87e109144cdc6e2e71f4fcad80c9cbf99879d8bb
deleted: sha256:0a2679c979afc5eb30764613ae1fa22199b872610f709f556b9f35bc0717e3f1
deleted: sha256:df64d3292fd6194b7865d7326af5255db6d81e9df29f48adde61a918fbd8c332

Total reclaimed space: 1.507GB
$ docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
registry     2         6a3edb1d5eb6   9 months ago   25.4MB

Answer will be: 1
```

Question:
```bash
Now we can pull images from our registry-server as well. Use docker pull [server-addr/image-name] to pull the images that we pushed earlier.

In our case we can use: docker pull localhost:5000/nginx
```

Answer:
```bash
This one, won't work; just press "Ok"

$ docker pull localhost:5000/nginx
Using default tag: latest
Error response from daemon: Get "http://localhost:5000/v2/": dial tcp 127.0.0.1:5000: connect: connection refused
$ curl -X GET localhost:5000/v2/_catalog
curl: (7) Failed to connect to localhost port 5000: Connection refused
$ docker pull registry-server:5000/nginx
Using default tag: latest
Error response from daemon: Get "https://registry-server:5000/v2/": dial tcp: lookup registry-server on 172.25.0.1:53: no such host
```

Question:
```bash
Let's clean up after ourselves.
Stop and remove the my-registry container.
```

Answer:
```bash
$ docker ps -a 
CONTAINER ID   IMAGE        COMMAND                  CREATED          STATUS                     PORTS     NAMES
699adcdf5d8e   registry:2   "/entrypoint.sh /etc…"   15 minutes ago   Exited (2) 5 minutes ago             my-registry
$ docker rm my-registry
my-registry
```

## Authors
- [@tnader1991](https://www.github.com/tnader1991)
