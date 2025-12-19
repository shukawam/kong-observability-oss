# Kong Observability w/ OSS

This is a sample configuration for experiencing Kong's observability using open-source software(OSS).

## Architecture

```mermaid
flowchart LR

    subgraph Kong Gateway
        A1[OpenTelemetry plugin]
    end

    A1 --> |OTLP Receiver| B1[OpenTelemetry Collector]

    B1 --> |OTLP Exporter| C1[Grafana Tempo]
    B1 --> |Prometheus Exporter| C2[Prometheus]
    B1 --> |OTLP Exporter| C3[Grafana Loki]

    C1 --> D1[Grafana]
    C2 --> D1
    C3 --> D1
```

## How to use?

Run this script.

```sh
docker compose up -d
```

After that, you can access as follows.

| service      | endpoint                                                         |
| ------------ | ---------------------------------------------------------------- |
| Kong Manager | [http://localhost:8002](http://localhost:8002)                   |
| API          | [http://localhost:8000/mock/uuid](http://localhost:8000/mock/uuid) |
| Grafana      | [http://localhost:3000](http://localhost:3000)                   |
