# Mairie360

Welcome to the **Mairie360**! This repository contains the Docker Compose configuration for the Mairie360 application, which includes various services such as core, files, calendars, emails, projects, and messages. Additionally, PostgreSQL and Redis are used as dependencies for data management and caching.

## 🚀 Services

- **Core**: The central service responsible for handling business logic and essential operations.
- **Files**: Manages file storage and access.
- **Calendars**: Handles all calendar-related functionalities.
- **Emails**: Manages email services.
- **Projects**: Manages project-related operations.
- **Messages**: Handles messaging services.
- **PostgreSQL**: Relational database used for storing structured data.
- **Redis**: In-memory data store used for caching and message brokering.
- **Nginx**: A reverse proxy that serves as the frontend for other services.

## 🔧 Configuration

### Volumes
- **`postgres-data`**: Persists PostgreSQL data.
- **`redis-data`**: Persists Redis data.

### Networks
- **`backend`**: Network for communication between backend services.
- **`frontend`**: Network for communication with the frontend (e.g., Nginx).

### Environment Variables
The following common environment variables are defined under `x-common-env` and shared across services:

- **`HOSTNAME`**: The hostname for the services.
- **`PORT`**: The port on which the services run.
- **`REDIS_URL`**: URL for connecting to the Redis service.
- **`CORE_PUBLIC_URL`**: URL for accessing the core service.

### Healthchecks
All services have healthchecks to ensure they are running smoothly. For example, the healthcheck for the **core** service is defined as:

```yaml
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost:3000"]
  interval: 10s
  timeout: 5s
  retries: 5
```

## 🛠️ Setup

### 1. Clone the repository:

```bash
git clone https://github.com/mairie360/mairie360.git
```

### 2. Navigate to the directory:

```bash
cd mairie360
```

### 3. Start the services:

```bash
docker compose up
```

This command will launch all the services in detached mode.

### 3. Access the services:

- **Nginx (frontend)**: [http://development.mairie360.fr](http://development.mairie360.com)

### 4. Stop the services:

```bash
docker-compose down
```

## ⚙️ Service Dependencies

- All services depend on **PostgreSQL** and **Redis** being healthy before they start.
- **Nginx** waits for the **files**, **calendars**, **emails**, **projects**, and **messages** services to be healthy before it starts.

## 🛠️ Customization

- You can modify the `nginx.conf` file to adjust the configuration of the Nginx reverse proxy.
- For each service, you can change the `POSTGRES_URL` to point to the appropriate PostgreSQL database.

---

Feel free to explore and modify this setup to suit your needs! 😊
```

This version adds a bit of polish with headings, icons, and consistent formatting. It should be easier to read and navigate!