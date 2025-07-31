# n8n - Dockerized Workflow Automation with PostgreSQL

This repository contains a minimal `docker-compose.yml` setup for running [n8n](https://n8n.io/) — an extendable workflow automation tool — with PostgreSQL as the database backend.

## 📦 Stack

- **n8n**: Open-source workflow automation tool
- **PostgreSQL**: Relational database for persistent storage
- **Docker & Docker Compose**: Container orchestration

## 🚀 Quick Start

### 1. Clone the repository

```bash
git https://github.com/kahnu044/n8n-docker
cd n8n-docker
````

### 2. Update environment variables (optional)

You can change the default username/password and DB credentials in the `docker-compose.yml` file.

### 3. Run the containers

```bash
docker-compose up -d
```

### 4. Access n8n

Open your browser and go to:

```
http://localhost:5678
```
Create an admin account first, then login using that credentials

## 🔧 Configuration

Here's a breakdown of the key environment variables:

### n8n

| Variable                       | Description                                    |
| ------------------------------ | ---------------------------------------------- |
| `N8N_BASIC_AUTH_ACTIVE`        | Enables basic authentication                   |
| `N8N_BASIC_AUTH_USER`          | Username for n8n login                         |
| `N8N_BASIC_AUTH_PASSWORD`      | Password for n8n login                         |
| `DB_TYPE`                      | Type of DB to use (`postgresdb`)               |
| `DB_POSTGRESDB_HOST`           | Hostname of the PostgreSQL container           |
| `DB_POSTGRESDB_PORT`           | Port of the PostgreSQL container               |
| `DB_POSTGRESDB_DATABASE`       | Database name                                  |
| `DB_POSTGRESDB_USER`           | Database user                                  |
| `DB_POSTGRESDB_PASSWORD`       | Database password                              |
| `NODE_FUNCTION_ALLOW_EXTERNAL` | Whitelisted external modules in Function nodes |

### PostgreSQL

| Variable            | Description   |
| ------------------- | ------------- |
| `POSTGRES_USER`     | DB username   |
| `POSTGRES_PASSWORD` | DB password   |
| `POSTGRES_DB`       | Database name |


## 💾 Persistent Data

PostgreSQL data is stored in a Docker volume named `db-data`, which ensures your data isn't lost when restarting containers.


## 📂 Folder Structure

```
.
├── docker-compose.yml     # Docker Compose config
└── README.md              # Project documentation
```

## 📌 Notes

* Make sure ports like `5678` (for n8n) and `5432` (for PostgreSQL) are not blocked or already in use.
* Change the credentials in a `.env` file or use Docker secrets for production deployments.

## 📃 License

This project is licensed under the [MIT License](https://opensource.org/license/mit).

## Author

[kahnu044](https://github.com/kahnu044/n8n-docker)
