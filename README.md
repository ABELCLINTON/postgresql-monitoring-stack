# PostgreSQL Monitoring Stack

A complete PostgreSQL monitoring and alerting stack built with Docker Compose, Prometheus, Grafana, and postgres_exporter.

This project demonstrates real-time database observability, metrics collection, dashboard visualization, and automated alerting in a containerized DevOps environment.

# Architecture

PostgreSQL → postgres_exporter → Prometheus → Grafana

## Workflow

* PostgreSQL generates database metrics
* postgres_exporter exposes PostgreSQL metrics
* Prometheus scrapes and stores metrics
* Grafana visualizes metrics using dashboards
* Prometheus alert rules monitor database health

---

# Technologies Used

* PostgreSQL
* Prometheus
* Grafana
* Docker Compose
* postgres_exporter
* Docker Volumes
* Git & GitHub

---

# Features

* Real-time PostgreSQL monitoring
* Grafana dashboard visualization
* Prometheus metrics scraping
* PostgreSQL health alerting
* Docker container orchestration
* Persistent PostgreSQL storage using Docker volumes

# Project Structure

postgresql-monitoring-stack/
│
├── docker-compose.yml
├── alert_rules.yml
├── .gitignore
│
└── prometheus/
    └── prometheus.yml

# Prerequisites

Before running this project, ensure the following are installed:

* Docker Desktop
* Git

Verify installations:

```bash
docker --version
git --version
```

---

# Setup Instructions

## 1. Clone the Repository

git clone https://github.com/ABELCLINTON/postgresql-monitoring-stack.git
cd postgresql-monitoring-stack

## 2. Start the Monitoring Stack

docker compose up -d

## 3. Verify Running Containers

docker ps

Expected containers:

* postgres-db
* postgres-exporter
* prometheus
* grafana

---

# Access the Services

## Grafana

```text
http://localhost:3000
```

Default credentials:

```text
Username: admin
Password: admin
```
## Prometheus

```text
http://localhost:9090
```
---
## PostgreSQL Exporter Metrics

```text
http://localhost:9187/metrics
```
# Grafana Configuration
## Add Prometheus Data Source
1. Open Grafana
2. Navigate to:

   * Connections → Data Sources
3. Add Prometheus
4. Set URL to:

```text
http://prometheus:9090
```
5. Click:
   * Save & Test

## Import PostgreSQL Dashboard

1. Open Dashboards
2. Click:

   * New → Import
3. Use Dashboard ID:

```text
9628
```
4. Select the Prometheus data source
5. Click Import
---
# Prometheus Alert Rules
The project includes the following alerts:

## PostgreSQLDown
Triggers when PostgreSQL becomes unavailable.

## HighDatabaseConnections
Triggers when database connections exceed the configured threshold.

View alerts:

```text
http://localhost:9090/alerts
```
# Persistent Storage
Docker volumes are configured to preserve PostgreSQL data across container restarts.

```yaml
volumes:
  postgres_data:
```

# Testing Database Activity

Access PostgreSQL:

```bash
docker exec -it postgres-db psql -U admin -d monitoringdb
```

Create a sample table:

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50)
);
```

Insert sample data:

```sql
INSERT INTO users(name) VALUES('GrafanaTest');
```
View records:

```sql
SELECT * FROM users;
```
# Monitoring Verification

## Prometheus Query Example

Open Prometheus:

```text
http://localhost:9090
```

Query:

```text
pg_up
```

Expected result:

```text
1
```
## Transaction Metrics

Query:

```text
pg_stat_database_xact_commit

```
This metric increases as database transactions occur.

# Screenshots

## Grafana Dashboard

(Add screenshot here)

## Prometheus Alerts

(Add screenshot here)

## Docker Containers

(Add screenshot here)

# Future Improvements
* Deploy on AWS EC2
* Add GitHub Actions CI/CD
* Configure email or Slack alerts
* Add Nginx reverse proxy
* Enable HTTPS with SSL
* Deploy using Kubernetes
* Add Loki for centralized logging

# DevOps Skills Demonstrated
* Docker containerization
* Infrastructure monitoring
* Observability engineering
* Metrics collection
* Alerting configuration
* PostgreSQL administration
* Grafana dashboarding
* Docker volume persistence
* Git and GitHub workflow

# Author
Ezea Chigozie
