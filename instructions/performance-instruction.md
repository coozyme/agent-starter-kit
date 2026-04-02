# Performance Standards

Guidelines for building performant applications and identifying bottlenecks.

## General Principles

1. **Measure first** — Don't optimize without profiling
2. **Optimize the critical path** — Focus on what users experience
3. **Set performance budgets** — Define acceptable thresholds
4. **Monitor continuously** — Track metrics in production

## Frontend Performance

### Loading
- Lazy load images and non-critical JavaScript
- Use code splitting to reduce initial bundle size
- Optimize and compress images (WebP, AVIF)
- Minify CSS and JavaScript for production
- Use CDN for static assets

### Runtime
- Avoid layout thrashing (batch DOM reads/writes)
- Debounce/throttle expensive event handlers
- Use `requestAnimationFrame` for animations
- Virtualize long lists (render only visible items)

### Metrics
| Metric | Target | Tool |
|--------|--------|------|
| First Contentful Paint | < 1.8s | Lighthouse |
| Largest Contentful Paint | < 2.5s | Lighthouse |
| Cumulative Layout Shift | < 0.1 | Lighthouse |
| Time to Interactive | < 3.8s | Lighthouse |

## Backend Performance

### API Response Times
| Type | Target |
|------|--------|
| Simple read | < 100ms |
| Complex query | < 500ms |
| Write operation | < 200ms |
| Background job dispatch | < 50ms |

### Database
- Use indexes on frequently queried columns
- Avoid N+1 queries — use eager loading
- Use connection pooling
- Paginate all list queries
- Cache expensive queries

### Caching Strategy
```
Request → Check Cache → Hit? → Return cached
                      → Miss? → Compute → Store in cache → Return
```

| Level | Technology | TTL | Use For |
|-------|-----------|-----|---------|
| Browser | HTTP cache headers | Varies | Static assets |
| CDN | CloudFront, Cloudflare | Minutes-Hours | Public content |
| Application | Redis, Memcached | Seconds-Minutes | API responses |
| Database | Query cache | Seconds | Repeated queries |

### Connection Management
- Use connection pooling for databases
- Set appropriate timeouts for external services
- Implement circuit breakers for unreliable dependencies
- Close connections properly (no leaks)

## Profiling Tools

| Language | Tool |
|----------|------|
| JavaScript | Chrome DevTools, Node.js `--prof` |
| Python | cProfile, py-spy, memory_profiler |
| Go | pprof |
| Java | JProfiler, VisualVM |
| General | Datadog, New Relic, Grafana |
