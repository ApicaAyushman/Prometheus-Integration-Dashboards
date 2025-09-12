Got it! Here’s a **simple, clean README** that avoids mentioning Grafana and does not use tables, keeping it fully generic for Apica Ascent:

---

# Node Exporter Dashboard

## Overview

This dashboard provides essential system metrics using **Node Exporter**, including:

* CPU usage
* Memory usage
* Disk utilization
* Network traffic
* System load
* Uptime

It uses a **classic layout** and is lightweight.

---

## Installation

1. Navigate to Dashboards in Apica Ascent.
2. Click on New Dashboard and toggle the slider.
3. Enter the Dashboard URL: https://raw.githubusercontent.com/ApicaAyushman/Prometheus-Integration-Dashboards/refs/heads/main/node-exporter-2.json
4. Select the data source: Ascent Metrics and Save.

---

## Panels and Metrics

**CPU Usage (%)**
Query: `100 - (avg by(instance)(irate(node_cpu_seconds_total{mode='idle'}[5m])) * 100)`
Shows CPU usage across all cores as a percentage.

**Memory Usage (%)**
Query: `(node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes) / node_memory_MemTotal_bytes * 100`
Displays percentage of RAM currently in use.

**Disk Usage (%) per Mount**
Query: `100 - (node_filesystem_avail_bytes{fstype!~'tmpfs|overlay'} / node_filesystem_size_bytes{fstype!~'tmpfs|overlay'} * 100)`
Shows disk usage per mount point, ignoring temporary and overlay filesystems.

**Network Traffic (Bytes/sec)**
Query: `rate(node_network_receive_bytes_total[1m])` / `rate(node_network_transmit_bytes_total[1m])`
Displays incoming (RX) and outgoing (TX) network traffic per second.

**System Load**
Query: `node_load1`, `node_load5`, `node_load15`
Displays system load averages over 1, 5, and 15 minutes.

**Uptime**
Query: `node_time_seconds - node_boot_time_seconds`
Shows total uptime of the system since last boot.

---

## Notes

* Minimal and lightweight, suitable for small setups or testing.
* Requires Node Exporter metrics scraped by Prometheus.

