# Toll Calculator

This project entails a data processing pipeline where a Truck sends OBU (On Board Unit) data to a receiver service, which subsequently forwards the data to an Apache Kafka queue. A distance calculation service then retrieves data from Kafka to compute the distance traveled. This calculated distance is utilized by an invoicer service, which in turn invokes the invoice calculation service to compute charges based on the distance provided. Finally, the invoice service stores the data into a database.

> [!Note]
> I didnt write too much code documentation so if you are curious, just read the test cases if you re wondering how the existing functionality works

## How it works

### Installing tools

1. Protobuffers & GRPC

```sh
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

3. That you need to set the $GOPATH/bin directory in your path Just like this or whatever your go directly lives.

- And dont forget to install protobuf compiler

### install grafana

[See Here](https://grafana.com/docs/grafana/latest/)

### install the package dependencies

- protobuffer package & GRPC package

```
google.golang.org/protobuf google.golang.org/grpc/
```

### Setting the Environment

```env
AGG_HTTP_ENDPOINT=:4000
AGG_GRPC_ENDPOINT=:3001
AGG_STORE_TYPE=memory
```

### Installing Prometheus

Install Prometheus in a Docker container

```sh
docker run -p 9090:9090 -v ./.config/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
```

Installing prometheus golang client

```sh
go get github.com/prometheus/client_golang/prometheus
```

Installing Prometheus natively on your system

1. Clone the repository

```sh
git clone https://github.com/promtheus/prometheus.git
```

2. Install

```sh
cd prometheus
make build
```

3. Run the Prometheus deamon

```sh
./promtheus --config.file=<your_config_file>yml
```

4. **In the projects case that would be (running from inside the project directory)**

```sh
../prometheus/prometheus --config.file=.config/prometheus.yml
```

## Kafka

```sh
docker run --name kafka -p 9092:9092 -e ALLOW_PLAINTEXT_LISTENER=yes -e KAFKA_CFG_AUTO_CREATE_TOPICS_ENABLE=true bitnami/kafka:latest
```
