# Elasticsearch-kibana-docker

This project contains docker-compose file that let's you set up elasticsearch and kibana running on docker.

### Prerequisites

You need to have following software installed on your machine :
- docker engine 18.06.0+
- docker-compose 1.22.0+

## Getting Started

To run the compose file just go to the `elasticsearch-kibana-docker` directory and use `docker-compose up` command to launch it. Optionally you can use `-d` flag to detach the output form the current shell.
```
docker-compose up
```
```
docker-compose up -d
```

## Setting up users

After the compose is launched you will have to setup passwords for `kibana` and `elastic` users. You can do it either by those two ways :

1. Logging into elasticsearch container and using `elasticsearch-setup-passwords` :
   1. ` $ docker exec -it elastic-kibana-docker_elasticsearch_1 bash`
   2. ` $ cd bin`
   3. ` $ elasticsearch-setup-passwords` This will let you set up passwords as you wish. Check [reference](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-passwords.html) for more details.

2. If you are interested in generating random passwords you can also use `$ docker-compose exec` for this. Just execute `$ docker-compose exec elasticsearch bin/elasticsearch-setup-passwords auto --batch`. This will output generated passwords.

After it is done you have to set `kibana` user password in `kibana/config/kibana.yml` file to the one that was the result of previous command. After it is changed, restart `kibana` service using `$ docker-compose restart kibana` command.

