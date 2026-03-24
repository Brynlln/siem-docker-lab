# Docker SIEM Lab – Brute Force Detection

## Overview
This project simulates a lightweight SIEM system using Docker.

The lab demonstrates how to:
- Generate authentication logs
- Detect failed login attempts
- Trigger alerts for potential brute-force attacks

## Technologies Used
- Docker
- Ubuntu Container
- Bash

## Lab Steps

### 1. Deploy Container
```bash
docker run -dit --name siem-bruteforce-lab ubuntu:22.04 bash
```

### 2. Generate Failed Login Logs
```bash
mkdir -p /var/log && for i in 1 2 3 4 5; do echo "Failed password attempt" >> /var/log/auth.log; done
```

### 3. View Logs
```bash
tail /var/log/auth.log
```

### 4. Count Failed Attempts
```bash
grep "Failed password" /var/log/auth.log | wc -l
```

### 5. Trigger Alert
```bash
COUNT=$(grep -c "Failed password" /var/log/auth.log); if [ $COUNT -gt 3 ]; then echo "ALERT: Possible brute force attack detected"; fi
```

## Key Outcome
Successfully simulated and detected brute-force login attempts using Docker-based log generation, analysis, and alerting.

## Screenshots

### 1. Container Deployment
![Container](./screenshots/container.png)

### 2. Failed Login Logs
![Logs](./screenshots/logs.png)

### 3. Log Analysis
![Tail](./screenshots/tail.png)

### 4. Detection Count
![Count](./screenshots/count.png)

### 5. Alert Trigger
![Alert](./screenshots/alert.png)

## Resume Bullet
- Built a lightweight SIEM lab using Docker to simulate brute-force login attempts, analyze logs, and trigger alerts using Bash-based detection logic.
