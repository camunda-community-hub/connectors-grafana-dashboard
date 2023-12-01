[![Community Extension](https://img.shields.io/badge/Community%20Extension-An%20open%20source%20community%20maintained%20project-FF4700)](https://github.com/camunda-community-hub/community)
![Compatible with: Camunda Platform 8](https://img.shields.io/badge/Compatible%20with-Camunda%20Platform%208-0072Ce)
[![](https://img.shields.io/badge/Lifecycle-Stable-brightgreen)](https://github.com/Camunda-Community-Hub/community/blob/main/extension-lifecycle.md#stable-)

# Grafana dashboard for Camunda 8 Connector Runtime

This repository contains a Grafana dashboard for monitoring Camunda 8 Connector Runtime, as well
as a Docker Compose setup for running it locally.

## Prerequisites

- [Connector Runtime](https://github.com/camunda/connectors-bundle/tree/main/connector-runtime) is running
- The dashboard is compatible with Connector Runtime **0.20.0** or higher

## Run the dashboard

```shell
docker-compose up
```

This will start Grafana and Prometheus containers and import the dashboard.

Prometheus is configured to scrape metrics from Connector Runtime at http://localhost:8080/actuator/prometheus.
If you want to change the URL, update the [`prometheus.yml`](prometheus/prometheus.yml) file.

## Dashboard

The dashboard is available at http://localhost:3000/d/connectors-sm

### Outbound Connector metrics

![outbound connector metrics](img/dashboard-outbound.png)

- Connector invocation count by connector type
- Connector job outcomes
- Failed jobs by connector type
- Connector invocation rate
- Average & maximum connector execution time by connector type

### Inbound Connector metrics

![inbound connector metrics](img/dashboard_inbound.png)

- Connector activation and trigger count by connector type
- Connector trigger outcomes
- Number of process definitions checked
- Number of active connectors by connector type
- Connector trigger rate
- Webhook call duration

### Connector Runtime metrics

![connector_runtime_metrics](img/dashboard-runtime.png)

- Status (UP/DOWN)
- JVM memory usage
- Uptime
- Log events chart
- Job executor thread pool state chart
- Job executor queue size chart
