# Docker Essentials — Sample API

Node.js API containerized with Docker and PostgreSQL using Docker Compose.

## Project Structure

```text
sample-api/
├── app.js
├── Dockerfile
├── .dockerignore
├── compose.yaml
├── package.json
├── package-lock.json
└── README.md
```

`.env` and `node_modules/` are excluded from Git.

## Build

```bash
docker build -t sample-api:1.0.0 .
```

## Run

```bash
docker run -d --name api -p 3000:3000 sample-api:1.0.0
```

Test:

```bash
curl http://localhost:3000/health
```

Expected:

```text
OK
```

## Docker Compose

Start API and PostgreSQL:

```bash
docker compose up -d
```

Check services:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs
```

API shell:

```bash
docker compose exec api sh
```

Database check:

```bash
docker compose exec db psql -U postgres -d orders -c "\dt"
```

PostgreSQL data is stored in the named `pgdata` volume.

## Docker Hub

Image:

```text
rahulpht/sample-api:1.0.0
```

[Docker Hub Repository](https://hub.docker.com/r/rahulpht/sample-api?utm_source=chatgpt.com)

## Troubleshooting

### Port already in use

```bash
docker ps
docker rm -f api
```

### Check container logs

```bash
docker compose logs api
docker compose logs db
```

### Check Compose configuration

```bash
docker compose config
```

## Cleanup

```bash
docker compose down
```

Remove containers and database volume:

```bash
docker compose down -v
```
