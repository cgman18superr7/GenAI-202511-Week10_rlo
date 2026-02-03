# Docker Setup for n8n and PostgreSQL

This guide explains how to set up and run the n8n workflow automation tool with a PostgreSQL database using Docker Compose.

## Prerequisites
- Docker and Docker Compose installed

## Setup Steps

1. **Clone the repository** (if not already done):
   ```sh
   git clone <your-repo-url>
   cd GenAI-202511-Week10_rlo
   ```

2. **Configuration**
   - The `docker-compose.yml` file defines two services: `n8n` and `postgres`.
   - Environment variables can be customized in the `.env` file.
   - By default, n8n will be accessible at [http://localhost:5678](http://localhost:5678).

   **To use a different port (e.g., 3333):**
   Edit the `ports` section under the `n8n` service in `docker-compose.yml`:
   ```yaml
   ports:
     - "3333:5678"
   ```

3. **Start the services**
   ```sh
   docker compose up -d
   ```
   This will start both n8n and PostgreSQL in the background.

4. **Access n8n**
   - Open your browser and go to [http://localhost:5678](http://localhost:5678) (or your chosen port).

5. **Stop the services**
   ```sh
   docker compose down
   ```

## Data Persistence
- n8n and PostgreSQL data are stored in Docker volumes (`n8n_data`, `postgres_data`) for persistence across restarts.

## Customization
- Edit the `.env` file to set environment variables (e.g., authentication, timezone).
- For more options, see the [n8n environment variables documentation](https://docs.n8n.io/hosting/environment-variables/).

## Troubleshooting
- View logs for n8n:
  ```sh
  docker compose logs n8n --tail=100
  ```
- View logs for PostgreSQL:
  ```sh
  docker compose logs postgres --tail=100
  ```
- Check running containers:
  ```sh
  docker compose ps
  ```

---

For further help, see the official [n8n Docker documentation](https://docs.n8n.io/hosting/docker/).
