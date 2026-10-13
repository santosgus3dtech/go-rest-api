# Go REST API

🇧🇷 [Leia este README em Português (Brasil)](README.pt-BR.md).

Task management REST API built with Go, Gorilla Mux, GORM and SQLite.

![API flow](docs/images/api-flow.svg)

## What It Shows

- RESTful CRUD endpoints.
- Layered project structure with routes, handlers, models and database setup.
- SQLite persistence through GORM.
- Docker-friendly local development.

## Project Structure

```text
go-rest-api/
  db/
  handlers/
  models/
  routes/
  dockerfile
  docker-compose.yml
  go.mod
  main.go
```

## Run Locally

```bash
go mod tidy
go run .
```

The API runs at:

```text
http://localhost:8080
```

## Run With Docker

```bash
docker compose up --build
```

## Endpoints

| Method | Route | Description |
| --- | --- | --- |
| `GET` | `/tasks` | List tasks |
| `GET` | `/tasks/{id}` | Get one task |
| `POST` | `/tasks` | Create a task |
| `PUT` | `/tasks/{id}` | Update a task |
| `DELETE` | `/tasks/{id}` | Delete a task |

## Example Requests

Create:

```bash
curl -X POST http://localhost:8080/tasks \
  -H "Content-Type: application/json" \
  -d "{\"title\":\"Write README\",\"description\":\"Document the API\",\"done\":false}"
```

List:

```bash
curl http://localhost:8080/tasks
```

Update:

```bash
curl -X PUT http://localhost:8080/tasks/1 \
  -H "Content-Type: application/json" \
  -d "{\"title\":\"Write README\",\"description\":\"Add examples\",\"done\":true}"
```

Delete:

```bash
curl -X DELETE http://localhost:8080/tasks/1
```

## Next Improvements

- Add unit tests around handlers.
- Add request validation.
- Add pagination and filtering.
- Expand the current GitHub Actions build/test checks with integration tests.
