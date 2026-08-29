---
layout: post
title: Monitoring
excerpt_separator:  <!--more-->
---

Some key take away on observability and monitoring

<!--more-->

### The 3 Pillars of Monitoring

Observability is often broken down into three pillars that together give a full picture of a system's health:

- **Metrics** - numeric measurements over time, such as CPU usage, Disk I/O, memory usage, request counts, or error rates, useful for spotting trends and triggering alerts.
- **Logs** - timestamped records of discrete events, useful for understanding exactly what happened at a specific point in time.

```bash
[2025-10-24 07:15:01] ERROR: User login failed — invalid password
[2025-10-24 07:16:05] INFO: Payment service connected to database
```

- **Traces** - end-to-end records of a request as it flows through a system, useful for pinpointing where time is spent or where failures occur in the system.

![Three pillars of monitoring](https://media.geeksforgeeks.org/wp-content/uploads/20260116154052682968/three_pillars_of_monitoring.webp)

### Key Monitoring Domains

#### Infrastructure (Health) Monitoring

**Purpose:** Ensure the underlying servers, storage, and network resources are healthy.

**Metrics:** CPU, RAM, disk space.

#### Application Performance Monitoring (APM)

**Purpose:** Identify application-level bottlenecks and errors.

**Metrics:** Request/transaction latency, error rates (HTTP 500s).

#### Log Monitoring

**Purpose:** Enable troubleshooting and querying of historical event data.

**Metrics:** Event dates, severity, details.

### How It Works

1. **Collection** - Agents are installed on the servers to collect metrics and log details (e.g. Splunk agents, or Metricbeat/Filebeat agents).
2. **Processing** - The collected data is sent, possibly enriched, and stored.
3. **Visualization** - The data is viewed, queried, and displayed using dashboards.
4. **Alerting** - Thresholds or conditions trigger alerts, notifying the right people by email or PagerDuty.

