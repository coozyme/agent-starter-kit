# Logging & Monitoring Standards

Guidelines for implementing effective logging, monitoring, and observability.

## Logging

### Log Levels
| Level | When to Use | Example |
|-------|------------|---------|
| `ERROR` | Something failed, needs attention | Database connection lost |
| `WARN` | Something unexpected but recoverable | Retry attempt, deprecated usage |
| `INFO` | Significant business events | User registered, order placed |
| `DEBUG` | Detailed diagnostic info (dev only) | Function inputs/outputs |

### Structured Logging
Always use structured (JSON) logging in production:
```json
{
  "timestamp": "2025-03-15T10:30:00Z",
  "level": "ERROR",
  "message": "Failed to process payment",
  "service": "payment-service",
  "request_id": "abc-123",
  "user_id": "user-456",
  "error": "Timeout after 10s",
  "metadata": {
    "amount": 99.99,
    "currency": "USD"
  }
}
```

### Logging Rules

```
✅ DO:
- Include request/correlation IDs for tracing
- Log at appropriate levels (not everything at INFO)
- Include enough context to debug without reproduction
- Use structured logging in production

❌ DON'T:
- Log sensitive data (passwords, tokens, PII)
- Use console.log in production code
- Log excessively (performance impact)
- Log inside tight loops
```

## Monitoring

### Key Metrics to Track
- **Error rate**: Percentage of failed requests
- **Latency**: P50, P95, P99 response times
- **Throughput**: Requests per second
- **Saturation**: CPU, memory, disk, connections usage

### Alerting Rules
| Condition | Severity | Action |
|-----------|----------|--------|
| Error rate > 5% | 🔴 Critical | Page on-call |
| P99 latency > 5s | 🟡 Warning | Notify team |
| CPU > 80% for 10min | 🟡 Warning | Investigate |
| Disk > 90% | 🔴 Critical | Immediate action |

### Health Checks
Every service should expose:
```
GET /health          → 200 OK (basic liveness)
GET /health/ready    → 200 OK (ready to serve traffic)
```

## Observability Stack

| Component | Purpose | Tools |
|-----------|---------|-------|
| Logging | Event records | ELK, CloudWatch, Datadog |
| Metrics | Quantitative measurements | Prometheus, Grafana, Datadog |
| Tracing | Request flow across services | Jaeger, Zipkin, OpenTelemetry |
