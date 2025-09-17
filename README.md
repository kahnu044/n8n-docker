# n8n - Dockerized Workflow Automation with PostgreSQL

This repository contains a minimal but production-ready `docker-compose.yml` setup for running [n8n](https://n8n.io/) — an extendable workflow automation tool — with PostgreSQL as the database backend and Adminer for DB management.

## 📦 Stack

- **n8n**: Open-source workflow automation tool
- **PostgreSQL**: Relational database for persistent storage
- **Adminer**: Lightweight database management tool
- **Docker & Docker Compose**: Container orchestration

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/kahnu044/n8n-docker
cd n8n-docker
````

### 2. Update environment variables (optional)

Edit the `docker-compose.yml` and adjust:

* `N8N_BASIC_AUTH_USER` and `N8N_BASIC_AUTH_PASSWORD` → set to a strong username & password
* PostgreSQL credentials (`POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`) if needed
* `N8N_HOST` and `WEBHOOK_URL` → set to your domain if using Nginx/SSL

> For production deployments, move credentials to a `.env` file or use Docker secrets.

### 3. Run the containers

```bash
docker compose up -d
```

### 4. Access n8n

* **Local:** [http://localhost:5678](http://localhost:5678)
* **With domain (via Nginx reverse proxy):** `http://n8n.yourdomain.com`

You’ll be prompted to create your **first admin account** inside n8n.

### 5. Access Adminer

Go to [http://localhost:8080](http://localhost:8080) and log in with:

```
System:   PostgreSQL
Server:   db
Username: n8n
Password: n8n
Database: n8n
```

## 🔧 Configuration

### n8n environment variables

| Variable                  | Description                                       |
| ------------------------- | ------------------------------------------------- |
| `N8N_BASIC_AUTH_ACTIVE`   | Enables basic authentication (`true`/`false`)     |
| `N8N_BASIC_AUTH_USER`     | Username for n8n login                            |
| `N8N_BASIC_AUTH_PASSWORD` | Password for n8n login                            |
| `DB_TYPE`                 | Database type (`postgresdb`)                      |
| `DB_POSTGRESDB_HOST`      | Hostname of the PostgreSQL container              |
| `DB_POSTGRESDB_PORT`      | PostgreSQL port (default `5432`)                  |
| `DB_POSTGRESDB_DATABASE`  | Database name                                     |
| `DB_POSTGRESDB_USER`      | Database user                                     |
| `DB_POSTGRESDB_PASSWORD`  | Database password                                 |
| `N8N_HOST`                | Domain for your n8n instance                      |
| `WEBHOOK_URL`             | Public URL for webhooks                           |
| `N8N_TRUSTED_PROXIES`     | Trusted proxy list (set to `0.0.0.0/0` for Nginx) |

### PostgreSQL environment variables

| Variable            | Description   |
| ------------------- | ------------- |
| `POSTGRES_USER`     | DB username   |
| `POSTGRES_PASSWORD` | DB password   |
| `POSTGRES_DB`       | Database name |

## 💾 Persistent Data

Data is stored in Docker volumes to ensure persistence:

* `db-data` → PostgreSQL data
* `n8n_data` → n8n workflows & credentials

## 📂 Folder Structure

```
.
├── docker-compose.yml     # Docker Compose config
└── README.md              # Project documentation
```

## 📌 Notes

* Ensure ports `5678` (n8n), `5432` (PostgreSQL), and `8080` (Adminer) are open.
* Use **Nginx reverse proxy** (recommended) to expose n8n securely with SSL.
* For production:

  * Always change default credentials.
  * Use `.env` files or Docker secrets.
  * Enable SSL via [Certbot](https://certbot.eff.org/) if using Nginx.

## 📃 License

This project is licensed under the [MIT License](https://opensource.org/license/mit).

## 👤 Author

[kahnu044](https://github.com/kahnu044/n8n-docker)