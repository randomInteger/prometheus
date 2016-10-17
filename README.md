NOTE:  This is a fork of the great work done by/at:  vegasbrianc/prometheus.  This fork exists only so that I could take vegasbrianc's project and configure it to meet my needs, then have my machines just grab the repo from here.  Please go to vegasbrianc/prometheus for all requests, bug reports, etc...  All work other than some config changes and this note was done by/at:  vegasbrianc/prometheus

# A Prometheus & Grafana docker-compose stack
Here's a quick start to stand-up a [Prometheus](http://prometheus.io/) stack containing Prometheus, Grafana and Node scraper to monitor your Docker infrastructure. A big shoutout to [philicious](https://github.com/philicious) for kicking this project off!

##Pre-requisites
Before we get started installing the Prometheus stack. Ensure you install the latest version of docker and [docker-compose](https://docs.docker.com/compose/install/) on your Docker host machine. This has also been tested with Docker for Mac and it works well.

##Installation & Configuration
Clone the project locally to your Docker host. 

If you would like to change which targets should be monitored or make configuration changes edit the [/prom/prometheus.yml](https://github.com/vegasbrianc/prometheus/blob/version-2/prometheus/prometheus.yml) file. The targets section is where you define what should be monitored by Prometheus. The names defined in this file are actually sourced from the service name in the docker-compose file. If you wish to change names of the services you can add the "container_name" parameter in the `docker-compose.yml` file. 

Once configurations are done let's start it up. From the /prometheus project directory run the following command:

    $ docker-compose up -d


That's it. docker-compose builds the entire Grafa and Prometheus stack automagically. 

The Grafana Dashboard is now accessible via: `http://<Host IP Address>:3000` for example http://192.168.10.1:3000

username - admin
password - foobar (Password is stored in the `config.monitoring` env file)

## Post Configuration
Now we need to create the Prometheus Datasource in order to connect Grafana to Prometheues 
* Click the `Grafana` Menu at the top left corner (looks like a fireball)
* Click `Data Sources`
* Click the green button `Add Data Source`.

<img src="https://github.com/vegasbrianc/prometheus/blob/version-2/images/Add_Data_Source.png" width="400" heighth="400">

## Install Dashboard
Use the dashboards in the /dashboards folder, rev6 is a good starting point.
