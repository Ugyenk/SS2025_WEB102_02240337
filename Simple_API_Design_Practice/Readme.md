# Student API Example (Node.js + Express)

This API demonstrates how to handle HTTP requests using Node.js (`http` module) and Express. It provides endpoints to fetch student data.

## Endpoints

### Part 1: Using HTTP Module

- **GET** `/`: Returns a list of students.

  Example response:
  ```json
  [
    { "id": 1, "name": "Karma", "age": 22 },
    { "id": 2, "name": "Sonam", "age": 26 }
  ]
  ```

### Part 2: Using Express

- **GET** `/students`: Returns all students.
- **GET** `/students/:id`: Returns a specific student by ID.

  Example response (for `/students/1`):
  ```json
  { "id": 1, "name": "takchey", "age": 24, "course": "Software Engineering" }
  ```

## Setup

1. Clone the repository.
2. Run `npm install express`.
3. Start the server with `node <file-name>.js`.

Server will run on `http://localhost:3000`.

## License

MIT License
