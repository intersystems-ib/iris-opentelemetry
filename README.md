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

# Monitoring tools:

## Prometheus
Prometheus docker image provide a web interface accessible from this [url](http://localhost:9090/). From the web interface you will be able to get all metrics available from IRIS instance, if you want to know more about these metrics check it [here](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=GCM_rest#GCM_rest_metrics_table). To get any metrics you only have to write the name of the metric and Prometheus will show all metrics to fetch.
![image](https://github.com/intersystems-ib/iris-opentelemetry/blob/main/images/prometheus-query.png)

![image](https://github.com/intersystems-ib/iris-opentelemetry/blob/main/images/prometheus-result.png)

## Jaeger
Jaeger is an Open Source software to monitorize traces from your solutions. As Prometheus, Jaeger has a web interface published [here](http://localhost:16686/search).

In our example we are going to use the method *TestTraces()* from SYS.Monitor.OTel class (more info [here](https://docs.intersystems.com/iris20251/csp/docbook/DocBook.UI.Page.cls?KEY=AOTEL#AOTEL_errors)). To execute this method you only have to open a terminal season from your Visual Studio Code (if your local project un VSCode is connected to the IRIS Server in Docker)
![image](https://github.com/intersystems-ib/iris-opentelemetry/blob/main/images/prometheus-result.png).

As soon as Jaeger find out a trace on OpenTelemetry Collect it will be available for consultancy from the web interface:
![image](https://github.com/intersystems-ib/iris-opentelemetry/blob/main/images/jaeger-otel.png).

By default, a Service is created with the name *irisotel* when a trace from IRIS is found in OpenTelemetry Collector.