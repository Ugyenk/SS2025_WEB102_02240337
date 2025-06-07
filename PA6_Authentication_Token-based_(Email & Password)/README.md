# Authentication API with JWT

A simple REST API for email/password authentication using TypeScript, Hono, PostgreSQL, and JWT tokens.

## What It Does

- User registration with email and password
- Secure password storage using bcrypt
- Login with JWT token generation
- Protected routes that require authentication
- Account balance management

## Getting Started

### Prerequisites
- Bun runtime
- PostgreSQL database
- Basic knowledge of REST APIs

### Setup
1. Clone the repository
```bash
git clone https://github.com/rubcstswe/web102-hono-auth-jwt-prisma-forked.git
cd web102-hono-auth-jwt-prisma-forked
bun install
```

2. Setup database
```bash
bunx prisma db push
bunx prisma generate
```

3. Start the server
```bash
bun run dev
```

Server runs on `http://localhost:3000`

## Database Structure

### User Table
- id: Unique identifier
- email: User's email (unique)
- hashPassword: Encrypted password

### Account Table
- id: Unique identifier
- userId: Links to user
- balance: Account balance (starts at 0)

Each user can have multiple accounts.

## API Endpoints

### Public Routes
- `POST /register` - Create new user
- `POST /login` - Login and get JWT token

### Protected Routes (requires JWT token)
- `GET /protected/account/balance` - Get user's account info

## How It Works

### Registration
1. User sends email and password
2. Password gets encrypted with bcrypt
3. User and default account created in database
4. Success message returned

### Login
1. User sends email and password
2. System checks if email exists
3. Password verified against stored hash
4. If valid, JWT token created (expires in 1 hour)
5. Token returned to user

### Accessing Protected Routes
1. Include JWT token in Authorization header
2. Middleware verifies token
3. If valid, access granted

## Example Usage

### Register a User
```bash
curl -X POST http://localhost:3000/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "mypassword"
  }'
```

### Login
```bash
curl -X POST http://localhost:3000/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "mypassword"
  }'
```

### Get Account Balance
```bash
curl -X GET http://localhost:3000/protected/account/balance \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

## Security Features

- Passwords are never stored as plain text
- JWT tokens expire after 1 hour
- Protected routes require valid authentication
- Proper error handling without revealing sensitive info

## Key Code Examples

### Password Hashing
```typescript
const bcryptHash = await Bun.password.hash(body.password, {
  algorithm: "bcrypt",
  cost: 4,
});
```

### JWT Token Creation
```typescript
const payload = {
  sub: user.id,
  exp: Math.floor(Date.now() / 1000) + 60 * 60, // 1 hour
};
const token = await sign(payload, secret);
```

### Route Protection
```typescript
app.use("/protected/*", jwt({ secret: 'mySecretKey' }));
```

## Important Notes

- Change the secret key in production
- Use HTTPS in production
- Consider adding rate limiting
- Validate all user inputs
- Store secrets in environment variables

This is a basic implementation perfect for learning authentication concepts!