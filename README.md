![Image of docker ps](https://github.com/darox/Grafana-Playground/blob/master/img/grafana.png)
# Grafana-Playground
This repository was created with the aim to make the start into Grafana easier. Grafa-Playground provides a full end-to-end environment to play around on your local machine. Spinning up the envrionment just takes a few minutes. The only requirements are a working internet connection and Docker + Docker Compose installed. 

The environment was tested on Ubuntu 20.04 and Docker Desktop with Windows Version 10.0.19041 Build 19041.


## Getting started

If you haven't already installed Docker and Docker Compose. Follow the official documentation to install Docker https://docs.docker.com/get-docker/ and Docker Compose https://docs.docker.com/compose/install/. 

## Get the repo

Clone this repo
```
git clone https://github.com/darox/Grafana-Playground
```

## Spin up the environment

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


## The real stuff

Open a webbrowser and head over to http://localhost:3000 in order to login to Grafana. The initial login credentials are admin/admin, but you will be prompted to set a new password. Go to configuration --> Data Sources --> Add Data Source --> InfluxDB. In fact there are only three things you have to configure:
Name: telegraf,
URL: http://influxdb:8086,
Database: telegraf

In a production environment it's highly recommended to configure username, password and TLS. 


Time to set up our first dashboard. Go to the dashbaord section in Grafana and click import. Luckily you don't have to create one by yourself. There's a file called telegraf.json in the folder grafana/dashboards. Copy the content of this file and paste it into the form and hit load. The metrics gathered by Telegraf are presented to you. Congratulations, you have your first Grafana environment up and ready!








