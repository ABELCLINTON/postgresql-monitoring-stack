# PostgreSQL Monitoring Stack

A complete PostgreSQL monitoring and alerting stack built with Docker Compose, Prometheus, Grafana, and postgres_exporter.

This project demonstrates real-time database observability, metrics collection, dashboard visualization, and automated alerting in a containerized DevOps environment.

---

# Architecture

PostgreSQL → postgres_exporter → Prometheus → Grafana

- PostgreSQL generates database metrics
- postgres_exporter exposes PostgreSQL metrics
- Prometheus scrapes and stores metrics
- Grafana visualizes metrics with dashboards
- Prometheus Alert Rules monitor database health

---

# Technologies Used

- PostgreSQL
- Prometheus
- Grafana
- Docker Compose
- postgres_exporter

---

# Features

- Real-time PostgreSQL monitoring
- Grafana dashboard visualization
- Prometheus metrics scraping
- PostgreSQL health alerting
- Docker container orchestration
- Persistent PostgreSQL storage using Docker volumes

---

# Project Structure

```bash
postgresql-monitoring-stack/
│
├── docker-compose.yml
├── alert_rules.yml
├── .gitignore
│
└── prometheus/
    └── prometheus.yml
