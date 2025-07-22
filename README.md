# NestJS Task Management API

A simple REST API for managing tasks with user authentication, built with NestJS and PostgreSQL.

## Features

- User registration and login with JWT
- Create, read, update, and delete tasks
- Users can only access their own tasks
- Input validation and error handling

## Tech Stack

- NestJS + TypeScript
- PostgreSQL + Prisma ORM
- JWT Authentication
- bcrypt for password hashing

## Setup

1. **Clone and install**

```bash
git clone https://https://github.com/aakamshpm/task-api-with-nestjs
cd task-api-with-nestjs
npm install
```

2. **Environment variables**
   Create `.env` file:

```env
DATABASE_URL="postgresql://username:password@localhost:5432/nestjs_tasks"
JWT_SECRET="your-jwt-secret"
JWT_EXPIRES_IN="7d"
PORT=3000
```

3. **Database setup**

```bash
npx prisma migrate dev --name init
npx prisma generate
```

4. **Run the app**

```bash
npm run start:dev
```

API runs at `http://localhost:3000/api`

## API Endpoints

### Authentication

```http
POST /api/auth/register
POST /api/auth/login
```

### Tasks (requires JWT token)

```http
GET    /api/tasks
POST   /api/tasks
GET    /api/tasks/:id
PATCH  /api/tasks/:id
DELETE /api/tasks/:id
```

## Example Usage

**Register:**

```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email":"user@test.com","password":"password123","name":"John"}'
```

**Create Task:**

```bash
curl -X POST http://localhost:3000/api/tasks \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{"title":"Learn NestJS","priority":"HIGH"}'
```

## Task Object

```json
{
  "id": "string",
  "title": "string",
  "description": "string (optional)",
  "completed": "boolean",
  "priority": "LOW | MEDIUM | HIGH",
  "dueDate": "ISO date string (optional)",
  "createdAt": "date",
  "updatedAt": "date"
}
```

## License

MIT
