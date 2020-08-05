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
docker compose up

```

The environment can also be started in the background with the option -d

```

docker compose up -d

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

## Bonus

So far the envrionment is not ready for storing logfiles. But we will change this with the help of Loki. Loki is a distributed logfile aggregation system which is maintained by Grafana Labs. Install the Loki docker logging driver 

```
docker plugin install grafana/loki-docker-driver:latest --alias loki --grant-all-permissions

```

Check if the logging driver is installed and enabled

```
docker plugin ls

```

As soon Grafana is ready add the Loki data source with url: http://loki:3100. there's a premade Loki Dashboard in the Grafana folder available. This dashboard shows all lines containg the word "error" for the Grafana, Influxdb and Telegraf container. 


Note that in the free version of Docker, only one logging driver can be specified. If you run the command 

```
docker logs grafana-playground_1
```

and the logging driver is set to Loki, nothing will be returned. Uncomment the section if you want to check for errors with

```
docker logs
```


## Permissions

If you prefer to run docker commands without root escalation, add your user to the Docker group.
```
sudo usermod -aG docker dario
```









