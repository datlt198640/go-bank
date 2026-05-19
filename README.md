# go-bank

A RESTful banking backend API built in Go, covering account management, multi-currency support, secure money transfers with deadlock-safe transactions, and token-based authentication.

## Tech Stack

- **Backend:** Go, Gin
- **Database:** PostgreSQL, sqlc (type-safe SQL codegen), golang-migrate
- **Auth:** PASETO v2 + JWT (access token)
- **Testing:** testify, gomock (mockgen)
- **Infra:** Docker, Docker Compose


## Quick Start

**1. Start PostgreSQL**

```bash
make postgres   # runs postgres:12-alpine on port 5432
make createdb   # creates the "simplebank" database
```

**2. Run database migrations**

```bash
make migrateup
```

**3. Configure environment**

```bash
cp app.env.example app.env   # set DB_SOURCE, SERVER_ADDRESS, TOKEN_SYMMETRIC_KEY
```

**4. Start the server**

```bash
make server
```

The API will be available at `http://localhost:8080`.

## Running Tests

```bash
make test
```

Runs all unit and integration tests with coverage report. Database layer is tested against a real PostgreSQL instance; API layer uses mock stores via `gomock`.

## Regenerate SQL Code

If you modify `.sql` query files under `db/query/`, regenerate the type-safe Go code with:

```bash
make sqlc
```
