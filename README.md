# OpenTelemetry Configuration Project
This is a project for training purposes. The main goal is to show how to configure Open Telemetry for an InterSystems IRIS instance.

# What do you need to install?

* [Git](https://git-scm.com/downloads)

* [Docker](https://www.docker.com/products/docker-desktop) (if you are using Windows, make sure you set your Docker installation to use "Linux containers").

* [Docker Compose](https://docs.docker.com/compose/install/)

* [Visual Studio Code](https://code.visualstudio.com/download) + [InterSystems ObjectScript VSCode Extension](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript)

# Docker images

The project deploys four docker containers:

* [InterSystems IRIS](https://containers.intersystems.com/contents): Data platform to be monitored.

* [OpenTelemetry Collector](https://opentelemetry.io/docs/collector/): Metrics, traces and logs collector.

* [Prometheus](https://prometheus.io/): Tool for metrics monitorization.

* [Jaeger](https://www.jaegertracing.io/): Tool for traces monitorization.


# Setup

Build the image that we will use during the workshop:
  
```console

$ git clone https://github.com/intersystems-ib/iris-opentelemetry
$ cd iris-opentelemetry
$ docker compose build

```
Now we just need to deploy the containers:
```console

$ docker compose up -d

```
If you are using Docker Desktop you should see a screen similar to this:

![image](https://github.com/intersystems-ib/iris-opentelemetry/blob/main/images/docker-desktop.png)

Already ready!