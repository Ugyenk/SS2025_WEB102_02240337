# Student Records API (Node.js, Express, Prisma, PostgreSQL)

A backend API for managing student records using Node.js, Express, Prisma, and PostgreSQL.

---

## Tech Stack

- **Backend:** Node.js, Express  
- **Database:** PostgreSQL  
- **ORM:** Prisma  

---

## Setup Instructions

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Set up Prisma and PostgreSQL:**
   - Create a PostgreSQL database and add the connection URL to `.env`:
     ```
     DATABASE_URL="postgresql://username:password@localhost:5432/student_records"
     ```
   - Run Prisma migrations:
     ```bash
     npx prisma migrate dev
     ```

3. **Start the server:**
   ```bash
   node index.js
   ```
   Server will run at `http://localhost:5100`.

---

## API Endpoints

- **GET `/students`**: Fetch all students.
- **GET `/students/:id`**: Fetch a student by ID.
- **POST `/students`**: Add a new student.  
  Request body (JSON):
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "course": "Computer Science",
    "enrollment_date": "2024-06-01"
  }
  ```

---

## Prisma Schema

```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model students {
  id              Int      @id @default(autoincrement())
  name            String   @db.VarChar(100)
  email           String   @unique @db.VarChar(100)
  course          String   @db.VarChar(100)
  enrollment_date DateTime @db.Date
}
```
