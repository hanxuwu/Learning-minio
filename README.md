# Learning-minio

# Deploy MinIO on Docker Compose [![Slack](https://slack.min.io/slack?type=svg)](https://slack.min.io) [![Go Report Card](https://goreportcard.com/badge/minio/minio)](https://goreportcard.com/report/minio/minio) [![Docker Pulls](https://img.shields.io/docker/pulls/minio/minio.svg?maxAge=604800)](https://hub.docker.com/r/minio/minio/)

Docker Compose allows defining and running single host, multi-container Docker applications.

With Compose, you use a Compose file to configure MinIO services. Then, using a single command, you can create and launch all the Distributed MinIO instances from your configuration. Distributed MinIO instances will be deployed in multiple containers on the same host. This is a great way to set up development, testing, and staging environments, based on Distributed MinIO. 

## 1. Prerequisites

* Familiarity with [Docker Compose](https://docs.docker.com/compose/overview/).
* Docker installed on your machine. Download the relevant installer from [here](https://www.docker.com/community-edition#/download).

## 2. Run Distributed MinIO on Docker Compose

To deploy Distributed MinIO on Docker Compose, please download [docker-compose.yaml](https://github.com/minio/minio/blob/master/docs/orchestration/docker-compose/docker-compose.yaml?raw=true) to your current working directory. Note that Docker Compose pulls the MinIO Docker image, so there is no need to explicitly download MinIO binary. Then run one of the below commands

### GNU/Linux and macOS

```sh
docker-compose pull
docker-compose up
```

### Windows

```sh
docker-compose.exe pull
docker-compose.exe up
```

Each instance is now accessible on the host at ports 9001 through 9004, proceed to access the Web browser at http://127.0.0.1:9001/

### Notes

* By default the Docker Compose file uses the Docker image for latest MinIO server release. You can change the image tag to pull a specific [MinIO Docker image](https://hub.docker.com/r/minio/minio/).

* There are 4 minio distributed instances created by default. You can add more MinIO services (up to total 16) to your MinIO Compose deployment. To add a service
  * Replicate a service definition and change the name of the new service appropriately.
  * Update the command section in each service.
  * Update the port number to exposed for the new service. Also, make sure the port assigned for the new service is not already being used on the host.

  Read more about distributed MinIO [here](https://docs.min.io/docs/distributed-minio-quickstart-guide).

* MinIO services in the Docker compose file expose ports 9001 to 9004. This allows multiple services to run on a host.

### Explore Further
- [Overview of Docker Compose](https://docs.docker.com/compose/overview/)
- [MinIO Docker Quickstart Guide](https://docs.min.io/docs/minio-docker-quickstart-guide)
- [Deploy MinIO on Docker Swarm](https://docs.min.io/docs/deploy-minio-on-docker-swarm)
- [MinIO Erasure Code QuickStart Guide](https://docs.min.io/docs/minio-erasure-code-quickstart-guide)

login:

`http://127.0.0.1:9002/minio/login`

access key: minio

secret key: minio123

# How to using the docker

1. `docker login`

2. `docker image`

C:\Study\VScode\Learning-minio\Learning-minio>docker images
REPOSITORY              TAG                            IMAGE ID            CREATED             SIZE
outline                 v001                           d9fb57a2bcef        21 hours ago        1.16GB
localstack/localstack   latest                         811d70818c52        2 days ago          839MB
server                  latest                         8d146e0d463a        6 days ago          1.91GB
myapp                   latest                         55460579337f        6 days ago          1.91GB
node                    12-alpine                      5d187500daae        7 days ago          80.1MB
rabbitmq                3-management                   5788d93cd8ad        7 days ago          180MB
rabbitmq                latest                         fccef3ad38c5        7 days ago          150MB
python                  3.7                            023b89039ba4        2 weeks ago         918MB
postgres                latest                         f88dfa384cc4        2 weeks ago         348MB
redis                   latest                         de25a81a5a0b        2 weeks ago         98.2MB
minio/minio             RELEASE.2019-10-12T01-39-57Z   67fec10c1e88        3 weeks ago         51MB
skunder301/dockerhub    minio_image                    67fec10c1e88        3 weeks ago         51MB
lphoward/fake-s3        latest                         4e02458e1040        2 years ago         167MB

3. tag your image

```s
docker tag minio/minio:RELEASE.2019-10-12T01-39-57Z skunder301/dockerhub:minio_image
```

```s
docker push skunder301/dockerhub:minio_image
```