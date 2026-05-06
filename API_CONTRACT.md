# API Contract

Base URL: `http://localhost:8000/api/v1`
Auth: Bearer token in `Authorization` header

---

## Auth

### POST /auth/register
**Body:** `{ "email": "user@example.com", "password": "string" }`
**Response 201:** `{ "id": "uuid", "email": "string" }`

### POST /auth/login
**Body:** `{ "email": "string", "password": "string" }`
**Response 200:** `{ "access_token": "string", "token_type": "bearer" }`

---

## Todos (all require Authorization header)

### GET /todos
**Response 200:** `[{ "id": "uuid", "title": "string", "is_done": bool, "created_at": "datetime" }]`

### POST /todos
**Body:** `{ "title": "string" }`
**Response 201:** `{ "id": "uuid", "title": "string", "is_done": false, "created_at": "datetime" }`

### PATCH /todos/{id}
**Body:** `{ "title": "string (optional)", "is_done": "bool (optional)" }`
**Response 200:** `{ "id": "uuid", "title": "string", "is_done": bool, "created_at": "datetime" }`

### DELETE /todos/{id}
**Response 204:** No content