# OpenTelemetry Recievers
Receivers collect telemetry from one or more soures. They can be push or pull based, and may support one or more data sources.

the following examples show the various receivers in the same configuration file:


**Note** : Configuring a receiver does not enable it. Receivers are enabled by adding them to the appropriate pipelines within the service section
```yaml
receivers:
  # Data sources: logs
  fluentforward:
    endpoint: 0.0.0.0:8006

  # Data sources: metrics
  host_metrics:
    scrapers:
      cpu:
      disk:
      filesystem:
      load:
      memory:
      network:
      process:
      processes:
      paging:

  # Data sources: traces
  jaeger:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      thrift_binary:
      thrift_compact:
      thrift_http:

  # Data sources: traces, metrics, logs
  kafka:
    protocol_version: 2.0.0

  # Data sources: traces, metrics
  opencensus:

  # Data sources: traces, metrics, logs
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
        tls:
          cert_file: cert.pem
          key_file: cert-key.pem
      http:
        endpoint: 0.0.0.0:4318

  # Data sources: metrics
  prometheus:
    config:
      scrape_configs:
        - job_name: otel-collector
          scrape_interval: 5s
          static_configs:
            - targets: [localhost:8888]

  # Data sources: traces
  zipkin:
```

