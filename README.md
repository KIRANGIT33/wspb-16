# Expense Tracker

Expense Tracker is the Web Software Production course project.

- `client/` — React + Vite + TypeScript frontend
- `server/` — Node + Express + TypeScript backend
- PostgreSQL — database storage

Each part is an independent npm project with its own `node_modules` and Biome configuration.

## Running

### Database

Start the PostgreSQL database from the project root:

```bash
docker compose up -d db
```

### Server

The server runs at http://localhost:3001.

```bash
cd server
npm install
npm run dev
```

The server uses PostgreSQL for storage through the connection pool in `src/db/pool.ts`.

Database connection settings are configured using environment variables such as:

- `PGHOST`
- `PGPORT`
- `PGUSER`
- `PGPASSWORD`
- `PGDATABASE`

Available expense endpoints:

| Method | Path | Description |
| --- | --- | --- |
| GET | `/api/expenses` | List expenses |
| POST | `/api/expenses` | Create an expense |
| PUT | `/api/expenses/:id` | Update an expense |
| DELETE | `/api/expenses/:id` | Delete an expense |

Available category endpoints:

| Method | Path | Description |
| --- | --- | --- |
| GET | `/api/categories` | List categories |
| POST | `/api/categories` | Create a category |
| PUT | `/api/categories/:id` | Update a category |
| DELETE | `/api/categories/:id` | Delete a category |

You can test the API directly:

```bash
curl http://localhost:3001/api/expenses
```

### Client

The client runs at http://localhost:5173.

```bash
cd client
npm install
npm run dev
```

The server and database need to be running for the application to work correctly.

## Testing

The server has unit and integration tests using Vitest and Supertest.

The tests use a separate PostgreSQL database called `app_test_db`, so test data is kept separate from development data.

Make sure the PostgreSQL database is running first:

```bash
docker compose up -d db
```

Then run the tests from the server directory:

```bash
cd server
npm test
```

The test suite includes tests for expense and category validation, expense mapping, and API routes.

## Linting

Biome handles linting and formatting.

Run from inside the client or server project:

```bash
npm run lint
npm run lint:fix
```
