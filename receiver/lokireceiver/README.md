# Loki Receiver

| Status                   |           |
| ------------------------ |-----------|
| Stability                | [alpha]   |
| Supported pipeline types | logs      |
| Distributions            | [contrib] |

The Loki receiver implements the [Loki push api](https://grafana.com/docs/loki/latest/clients/promtail/#loki-push-api) as specified [here](https://grafana.com/docs/loki/latest/api/#push-log-entries-to-loki). 
It allows Promtail instances to specify the open telemetry collector as their lokiAddress.

This receiver runs HTTP and GRPC servers to ingest log entries in Loki format.

## Getting Started

The settings are:

- `endpoint` (required, default = 0.0.0.0:3500 for grpc protocol, 0.0.0.0:3600 http protocol): host:port to which the receiver is going to receive data.
- `use_incoming_timestamp` (optional, default = false) if set `true` the timestamp from Loki log entry is used

Example:
```yaml
receivers:
  loki:
    protocols:
      http:
      grpc:
    use_incoming_timestamp: true
```

[alpha]:https://github.com/open-telemetry/opentelemetry-collector#alpha
[contrib]:https://github.com/open-telemetry/opentelemetry-collector-releases/tree/main/distributions/otelcol-contrib
