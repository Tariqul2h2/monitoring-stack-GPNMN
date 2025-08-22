# Monitoring Stack with Prometheus, Node Exporter, Grafana, MySQL & Nginx

This repo provides a **one-click monitoring solution** using Docker Compose.  
It includes:  

- **Prometheus** → collects metrics  
- **Node Exporter** → exports host system metrics  
- **Grafana** → dashboards & visualization  
- **MySQL** → Grafana backend database  
- **Nginx** → reverse proxy in front of Grafana  

Pre-configured to automatically:  
- Add **Prometheus** as a Grafana datasource  
- Import the **Node Exporter Full Dashboard (ID 1860)**  

---

## Folder Structure
```
monitoring-stack-GPNMN/
├── docker-compose.yml
├── .env
├── prometheus/
│   └── prometheus.yml
├── nginx/
│   └── nginx.conf
├── grafana/
│   ├── dashboards/
│   │   └── node-exporter.json
│   └── provisioning/
│       ├── datasources/
│       │   └── prometheus.yml
│       └── dashboards/
│           └── dashboards.yml
└── mysql/
    └── init.sql
```

---

## Quick Start

### 1. Clone this repo
```bash
https://github.com/Tariqul2h2/monitoring-stack-GPNMN.git
```

### 2. Start the stack
```bash
cd monitoring-stack-GPNMN
docker-compose up -d
```

---

##  Default Credentials

| Service   | Username | Password   |
|-----------|----------|------------|
| MySQL     | grafana  | grafana_pass |
| MySQL root | root     | root_pass   |
| Grafana   | admin    | secret     |

> You can change these in `.env`.

---

##  Access the services

- **Grafana** → [http://localhost:3000](http://localhost:3000)  
- **Prometheus** → [http://localhost:9090](http://localhost:9090)  
- **Node Exporter** → [http://localhost:9100/metrics](http://localhost:9100/metrics)  
- **MySQL** → exposed on port `3306`  

---

## 🔧 Customization

- Edit `.env` → change database & Grafana admin credentials  
- Edit `prometheus/prometheus.yml` → add new scrape targets  
- Edit `nginx/nginx.conf` → enable HTTPS, change domain, add auth, etc.  
- Add more dashboards in `grafana/dashboards/` and update `dashboards.yml`  

---

##  Stop & Remove

```bash
docker-compose down
```

If you also want to delete stored data (Grafana dashboards, MySQL DB):
```bash
docker-compose down -v
```

---

## ❤️  Contributing
Feel free to fork, submit PRs, or open issues if you have improvements.  
