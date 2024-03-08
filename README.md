# Toll Calculator

```sh
docker run --name kafka -p 9092:9092 -e ALLOW_PLAINTEXT_LISTENER=yes -e KAFKA_CFG_AUTO_CREATE_TOPICS_ENABLE=true bitnami/kafka:latest
```

## Installing GRPC and Protobuffer plugins for Golang.

1. Protobuffers

```sh
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
```

2. GRPC

```sh
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

3. That you need to set the /go/bin directory in your path Just like this or whatever your go directly lives.

- And dont forget to install protobuf compiler

## install the package dependencies

- protobuffer package & grpc package

```
google.golang.org/protobuf google.golang.org/grpc/
```

## Installing Prometheus

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

4. In the projects case that would be (running from inside the project directory)

```sh
../prometheus/prometheus --config.file=.config/prometheus.yml
```
