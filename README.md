<p align="center">
<a href="https://kafka.apache.org/" target="_blank"><img src="./images/logos/kafka-logo.png" alt="kafka Logo" width="120" ></a>
<a href="https://prometheus.io/" target="_blank"><img src="./images/logos/prometheus-logo.png" alt="Prometheus logo" width="120"/></a>
<a href="https://grafana.com/grafana/" target="_blank"><img src="./images/logos/grafana-logo.png" alt="Grafana logo" width="120"/></a>
<a href="https://www.conduktor.io/" target="_blank"><img src="./images/logos/conduktor-logo.png" alt="Conduktor logo"  width="140"/></a>
<a href="https://www.postgresql.org/" target="_blank"><img src="./images/logos/postgresql-logo.png" alt="Postgresql logo" width="120"/></a>
</p>

# Apache kafka Métrics #

Basic Configuration Environment for <a href="https://kafka.apache.org/" target="blank">Apache kafka</a> Metrics and monitoring.

## Description


<p align="center"><a href="https://kafka.apache.org/" target="blank">Apache kafka</a> Cluster Configuration with Metrics Visualization using JMX Exporter Agent, Connection and monitoring <a href="https://prometheus.io/" target="blank">Prometheus</a>, <a href="https://grafana.com/grafana/" target="blank">Grafana</a> and <a href="https://www.conduktor.io/" target="blank">Conduktor</a> in <a href="https://docs.docker.com/compose/" target="blank">Docker</a> Containers.</p>

## Requirements

Make sure you have the latest versions of **Docker** and **Docker Compose** installed on your machine.

Clone this repository or copy the files from this repository into a new folder. In the docker-compose.yml file, you can change the ports (in case you're running multiple containers on your system).

With this project, you can quickly run the following:

- [Apache Kafka](https://hub.docker.com/r/confluentinc/cp-kafka)
- [Prometheus](https://hub.docker.com/r/prom/prometheus)
- [Grafana](https://hub.docker.com/r/grafana/grafana)
- [Conduktor](https://hub.docker.com/r/conduktor/conduktor-platform)
- [Postgresql](https://hub.docker.com/_/postgres)

Contents:

- [Apache kafka Métrics](#apache-kafka-métrics)
  - [Description](#description)
  - [Requirements](#requirements)
  - [Configuration](#configuration)
  - [Installation](#installation)
  - [Use](#use)
    - [Prometheus](#prometheus)
    - [Grafana](#grafana)
    - [Conduktor](#conduktor)
  - [License](#license)


## Configuration

Edit the `.env` file to change the default environment variables.

## Installation

Open a terminal and run `cd` to the folder where you can see the files `docker-compose-single-config.yml`, which contains the necessary configuration to deploy a Kafka broker, and the file `docker-compose-multiple-config.yml`, which contains the configuration for multiple Apache Kafka brokers.

Execute as needed:

```
docker-compose -f docker-compose-single-config.yml up -d  
```

This will start the containers and create volumes according to the configuration in your `docker-compose.yml` files. **Make sure to grant write permissions to the directory** so it can create the necessary volumes for the containers. Similarly, **remember to clean the volumes folder when running different files to avoid data inconsistency**.

* `.env` – File containing the environment variable data.
* `volumenes` – Folder containing container data.
* `config` – Folder containing the configuration files necessary for the operation of the containers.

The containers are already built and running. You should be able to access the installation of each container.

## Use

### Prometheus

You can visit `http:/localhost:9090` to access **Prometheus** after starting the containers, and you will see a screen like the following, where you will have the option to add panels based on your custom `query`.


<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/prometheus-home.png" width="800" alt="prometheus"></p>
</a>

In the Status menu, you can see the status of your **Apache kafka broker** under `targets`.


<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/prometheus-state.png" width="800" alt="prometheus"></p>
</a>

### Grafana

You can visit `http:/localhost:3000` to access Grafana. The default username is **admin**, which is provided in the `.env` file, and the password is **admin**. Once you log in, it will prompt you to create a new password.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-login.png" width="800" alt="grafana"></p>
</a>

Once logged in, you will see a screen like the following:

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-home.png" width="800" alt="grafana"></p>
</a>

Where you will need to add your **Prometheus** data source as shown in the image.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-datasource.png" width="800" alt="grafana"></p>
</a>

You will select **Prometheus** as your data source.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-datasource2.png" width="800" alt="grafana"></p>
</a>

You will need to fill in the connection details for your **Prometheus** container.

To add a new dashboard to **Grafana**, select `New`, followed by `Import`, where you will choose the `dashboard-kafka.json` file located in the `config` folder, which is configured for the visualization of **Kafka metrics**.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-dashboard.png" width="800" alt="grafana"></p>
</a>

Once the file is imported, you will obtain the following screens with multiple panels and graphs representing the metrics of the **Apache Kafka** `cluster` and `brokers`.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-dashboard2.png" width="800" alt="grafana"></p>
</a>
<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-dashboard3.png" width="800" alt="grafana"></p>
</a>
<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/grafana-dashboard4.png" width="800" alt="grafana"></p>
</a>

### Conduktor 

You can visit `http:/localhost:8080` to access **Conduktor**. The default username is **admin@admin.io**, and the password is **admin**. You can modify these credentials in the environment variables located in the `.env` file.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/conduktor-login.png" width="800" alt="conduktor"></p>
</a>

The **Conduktor** tool will allow you to view the status of the cluster as well as visualize the **Apache Kafka** `brokers` you have deployed.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/conduktor-cluster.png" width="800" alt="conduktor"></p>
</a>

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/conduktor-brokers.png" width="800" alt="conduktor"></p>
</a>

**Conduktor** will be useful for conducting the necessary tests and visually managing **Apache Kafka**. You will be able to create new `topics` and send/consume `messages`.

<a href="https://github.com/ali-ramirez/kafka-metrics" rel="noreferrer">
<p style="text-align: center;"><img src="./images/conduktor-topic.png" width="800" alt="conduktor"></p>
</a>

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)
