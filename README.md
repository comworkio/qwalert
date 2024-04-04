# qwalert

Alerting module for [Quickwit](https://quickwit.io)

It's designed to work alongside with [Prometheus alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager) and with Prometheus alert configuration's style.

Example of configuration:

```yaml
groups:
  - name: logs_to_watch
    rules:
      - alert: WarningLogs
        expr: "severity:WARN"
        for: 1m
        labels:
          severity: medium
        annotations:
          summary: There is warning logs
          description: "There is warning logs (number of hits: {{ $value }})"
      - alert: ErrorLogs
        expr: "severity:ERROR"
        for: 1m
        labels:
          severity: high
        annotations:
          summary: There is error logs
          description: "There is error logs (number of hits: {{ $value }})"
```
