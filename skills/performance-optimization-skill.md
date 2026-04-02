---
name: Performance Optimization
description: Skill for identifying and resolving performance bottlenecks
---

# Performance Optimization Skill

Systematic approach to finding and fixing performance issues.

## When to Use This Skill

- When response times exceed acceptable thresholds
- When resource usage (CPU, memory) is too high
- When users report slow experiences
- During performance audits before launches

## Optimization Process

### 1. Define the Goal
- What metric needs to improve? (latency, throughput, memory)
- What is the acceptable target?
- What is the current baseline?

### 2. Profile & Measure
- Use profiling tools to identify bottlenecks
- Don't guess — let data guide optimization
- Focus on the hottest path first

### 3. Identify the Bottleneck
Common bottleneck categories:

| Category | Symptoms | Common Fixes |
|----------|----------|-------------|
| Database | Slow queries, high DB CPU | Add indexes, optimize queries |
| Network | High latency, timeouts | Cache, reduce calls, parallelize |
| CPU | High CPU usage | Optimize algorithms, offload |
| Memory | High memory, GC pauses | Fix leaks, reduce allocations |
| I/O | Slow reads/writes | Buffer, batch, async I/O |

### 4. Implement Fix
- Make one change at a time
- Benchmark before and after
- Ensure correctness is not sacrificed

### 5. Verify & Monitor
- Confirm the metric improved
- Check for side effects (increased memory, etc.)
- Set up monitoring to prevent regression

## Quick Wins Checklist

- [ ] Add database indexes for slow queries
- [ ] Enable compression (gzip/brotli)
- [ ] Implement caching for repeated computations
- [ ] Paginate large result sets
- [ ] Use connection pooling
- [ ] Lazy load non-critical resources
- [ ] Batch database operations
- [ ] Use async processing for non-critical tasks
