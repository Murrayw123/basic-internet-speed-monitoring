## What is this?

A very very basic POC for speedtest with Prometheus and Grafana

## Dependencies
- Docker https://docs.docker.com/engine/install/ubuntu/
- Docker compose plugin `sudo apt-get update && sudo apt-get install docker-compose-plugin`

## Running this
- Download from Github as a ZIP or run `git clone https://github.com/Murrayw123/basic-internet-speed-monitoring.git`
- In the main directory (internet-speed-monitoring) run `docker compose up`
- To run this in detached mode (background mode) `docker compose up -d`

## Basic debugging
- `docker ps` - there should be three containers
- Are both the prometheus endpoints healthy? `http://localhost:9000/targets`
- Test the datasource is active in http://localhost:3000/connections/datasources

## Basic wiring
- Everything is exposed onto the host, we're assuming nothing else is running on TCP 9000, 3000 and 9469
- The Docker Compose file specifies `securityisimportant` as the Grafana password
- There's a Prometheus data source added called Prometheus - Datasources.yaml
- The speedtest runs every 10 minutes. This is configurable by changing the value `scrape_interval: 10m` to something less / more obscene

All you need to do now is create a Dashboard, I figured you'd want to tinker with it anyway so I didn't bother saving one

![img.png](img.png)