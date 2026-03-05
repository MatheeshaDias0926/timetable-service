# Timetable Service — Smart Campus Services

Timetable Management microservice for the Smart Campus Services platform.

## Features

- **Auto-Generate Timetable** from enrolled courses (calls Course Service)
- **Manual Entry CRUD** — Add, update, delete timetable entries
- **Time Conflict Detection** — Prevents overlapping schedules
- **Group by Day** — Returns timetable organized by weekday
- **Inter-Service Auth** — JWT validation via Auth Service

## API Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| GET | `/timetable` | JWT | Get student's timetable |
| POST | `/timetable/generate` | JWT | Auto-generate from enrolled courses |
| POST | `/timetable` | JWT | Add entry manually |
| PUT | `/timetable/:id` | JWT | Update entry |
| DELETE | `/timetable/:id` | JWT | Remove entry |
| DELETE | `/timetable` | JWT | Clear entire timetable |
| GET | `/health` | No | Health check |

## Inter-Service Communication

1. **Auth Service**: Validates JWT tokens via `GET /auth/validate`
2. **Course Service**: Fetches enrolled courses via `GET /courses/my` for timetable generation

## Quick Start

```bash
npm install
cp .env.example .env
npm run dev     # http://localhost:3003
```

## Docker

```bash
docker-compose up --build
```

## Testing

```bash
npm test
```

## License

MIT
