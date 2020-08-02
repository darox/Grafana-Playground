# Grafana-Playground
This repository was created with the aim to make the start into Grafana easier. Grafa-Playground provides a full end-to-end environment to play around on your local machine. Spinning up the envrionment just takes a few minutes. The only requirements are a working internet connection and Docker + Docker Compose installed. 

## Getting started

If you haven't already installed Docker and Docker Compose. Follow the official documentation to install Docker https://docs.docker.com/get-docker/ and Docker Compose https://docs.docker.com/compose/install/. 

##Get the repo

Clone this repo with
```
git clone https://github.com/darox/Grafana-Playground
```

##Spin up the environment

Now it's time to spin up the environment. It makes sense to start the environment in the foreground to check for errors

```
sudo docker compose up

```

The environment can also be started in the background with the option -d

```

sudo docker compose up -d

```

Let's check if all containers are running

```

docker ps -a

```

Ideally it should look like this

![Image of docker ps](https://github.com/darox/Grafana-Playground/blob/master/img/docker-ps.png)









