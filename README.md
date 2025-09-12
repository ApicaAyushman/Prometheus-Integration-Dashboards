Perfect! Here's a **fully polished, professional README** for your Node Exporter dashboard—GitHub-ready, visually clear, and with all useful details:

---

# Node Exporter Dashboard

![Dashboard Screenshot](./screenshot.png)
*A classic, minimal Node Exporter dashboard*

---

## Overview

The **Node Exporter Dashboard** provides essential system metrics for Linux servers.

This dashboard monitors:

* CPU usage
* Memory usage
* Disk utilization
* Network traffic
* System load
* Uptime

It’s ideal for small environments, testing setups.

---

## Features

| Metric                          | Description                                                                |
| ------------------------------- | -------------------------------------------------------------------------- |
| **CPU Usage (%)**               | Overall CPU usage as a percentage across all cores.                        |
| **Memory Usage (%)**            | RAM used as a percentage of total memory.                                  |
| **Disk Usage (%) per Mount**    | Disk utilization per mount point, excluding tmpfs and overlay filesystems. |
| **Network Traffic (Bytes/sec)** | Incoming (RX) and outgoing (TX) network traffic per second.                |
| **System Load**                 | Average system load over 1, 5, and 15 minutes.                             |
| **Uptime**                      | How long the system has been running since last boot.                      |

---


> Your dashboard should now display real-time system metrics from Node Exporter.

---

## Prometheus Queries Explained

| Panel                        | Query                                                                                              | Explanation                                                                          |                     |                                                                   |
| ---------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------- | ----------------------------------------------------------------- |
| **CPU Usage (%)**            | `100 - (avg by(instance)(irate(node_cpu_seconds_total{mode='idle'}[5m])) * 100)`                   | Calculates CPU usage by measuring idle time and converting it to a usage percentage. |                     |                                                                   |
| **Memory Usage (%)**         | `(node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes) / node_memory_MemTotal_bytes * 100` | Computes RAM usage as a percentage of total memory.                                  |                     |                                                                   |
| **Disk Usage (%) per Mount** | \`100 - (node\_filesystem\_avail\_bytes{fstype!\~'tmpfs                                            | overlay'} / node\_filesystem\_size\_bytes{fstype!\~'tmpfs                            | overlay'} \* 100)\` | Disk usage per mount, ignoring temporary and overlay filesystems. |
| **Network Traffic**          | `rate(node_network_receive_bytes_total[1m])` / `rate(node_network_transmit_bytes_total[1m])`       | Shows network traffic in bytes per second for receive and transmit.                  |                     |                                                                   |
| **System Load**              | `node_load1`, `node_load5`, `node_load15`                                                          | Displays system load averages over 1, 5, and 15 minutes.                             |                     |                                                                   |
| **Uptime**                   | `node_time_seconds - node_boot_time_seconds`                                                       | Total uptime of the server in seconds since last boot.                               |                     |                                                                   |

---



---

## References

* [Node Exporter GitHub](https://github.com/prometheus/node_exporter)
* [Prometheus Query Language (PromQL)](https://prometheus.io/docs/prometheus/latest/querying/basics/)
* [Grafana Documentation](https://grafana.com/docs/)

