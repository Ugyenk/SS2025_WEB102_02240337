# Student Records API (Node.js + Express + PostgreSQL)

This is a simple backend API to manage student records using Node.js, Express, and PostgreSQL.

---

## Tech Stack

- **Backend:** Node.js, Express  
- **Database:** PostgreSQL  
- **Other:** `pg` (PostgreSQL client), `cors`

---

## Features

- Fetch all students (GET `/api/students`)
- Add a new student (POST `/api/students`)
- Simple root endpoint for server test

---

## Setup Instructions

1. **Install PostgreSQL** and create a database:

   ```sql
   CREATE DATABASE student_records;

   CREATE TABLE students (
       id SERIAL PRIMARY KEY,
       name VARCHAR(100),
       email VARCHAR(100) UNIQUE,
       course VARCHAR(100),
       enrollment_date DATE
   );
   ```

2. **Clone the project and install dependencies:**

   ```bash
   git clone <your-repo-url>
   cd student-records-api
   npm install
   ```

3. **Adjust PostgreSQL credentials in `index.js` if needed:**

   ```js
   const pool = new Pool({
     user: 'postgres',
     host: 'localhost',
     database: 'student_records',
     password: 'your_password',
     port: 5432
   });
   ```

4. **Run the server:**

   ```bash
   node index.js
   ```

   Server will run at: `http://localhost:5001`

---

## API Endpoints

### GET `/api/students`

Returns all students in the database.

### POST `/api/students`

Adds a new student. Required fields in JSON body:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "course": "Computer Science",
  "enrollment_date": "2024-06-01"
}
```

---

## Notes

- Make sure PostgreSQL is running locally.
- Email must be unique; duplicate emails will return a `409 Conflict` error.
