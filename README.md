# Mairie360 – Production Stack

This repository contains the **production-ready** Docker Compose setup for running the [Mairie360](https://github.com/mairie360) platform.

All services are prebuilt and configured to work together using containerized PostgreSQL, Redis, microservices, and NGINX as a reverse proxy.

---

## Overview

This stack is designed to **showcase the production result** of the Mairie360 platform.

### Included Services:

- `PostgreSQL` – Persistent relational database
- `Redis` – In-memory data store
- `Core` – The module orchestrator
- `Files` – Files management module
- `Calendars` – Calendar management
- `Emails` – Email management module
- `Projects` – Project management module
- `Messages` – Message management module
- `NGINX` – Reverse proxy for exposing services over HTTP

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/mairie360/mairie360.git
cd mairie360
```
---

### 3. Start the Stack

To deploy the full production environment:

```bash
docker compose up
```

All images are pulled from the GitHub Container Registry and set to auto-restart on failure.

---

## Accessing the Platform

By default, the stack exposes everything through NGINX on port **80**.

Open `http://development.mairie360.fr` to access the platform.

---

## Health Monitoring

Each service is monitored via built-in Docker healthchecks. To verify:

```bash
docker compose ps
```

All services should be marked as `healthy`.

---

## Updating the Stack

To update all services with the latest images:

```bash
docker compose pull
docker compose up -d
```

---

## Shutting Down

To stop all services:

```bash
docker compose down
```

To remove volumes as well (will delete all data):

```bash
docker compose down -v
```
