# Observability Stack — SigNoz + OpenTelemetry

> Seeing traffic and errors on a site that had neither.

## Problem

A marketing site handling live webinar traffic had zero visibility into performance. No metrics, no logs aggregation, no way to know if pages were slow or returning errors — until users complained.

## What I Built

An observability stack using SigNoz with OpenTelemetry collectors, wired into Caddy's structured access logs.

### Components

- **SigNoz** — open-source APM for traces, metrics, and logs in one UI
- **OpenTelemetry Collectors** — receive, process, and export telemetry data
- **Caddy structured logs** — JSON access logs piped to the OTel collector
- **Dashboards** — slow pages and 5xx spikes visible in one place

## Architecture

```
┌──────────┐     structured      ┌───────────────────┐
│  Caddy   │────── logs ────────►│  OTel Collector    │
│ (reverse │                     │  (receive/process) │
│  proxy)  │                     └────────┬───────────┘
└──────────┘                              │
                                          ▼
                                 ┌─────────────────┐
                                 │     SigNoz       │
                                 │  ┌────────────┐  │
                                 │  │  Traces    │  │
                                 │  │  Metrics   │  │
                                 │  │  Logs      │  │
                                 │  └────────────┘  │
                                 │   Dashboards +   │
                                 │   Alerts          │
                                 └─────────────────┘
```

## Outcome

Slow pages and 5xx spikes now visible in one place. The team sees problems before users report them.

## Stack

`SigNoz` · `OpenTelemetry` · `Caddy` · `Docker`

## Context

Built as Platform Engineer at [WeOwn](https://weown.net) (2025–present). Source code is proprietary.
