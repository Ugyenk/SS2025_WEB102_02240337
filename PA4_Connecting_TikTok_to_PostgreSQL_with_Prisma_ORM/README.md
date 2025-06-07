# Database Integration with PostgreSQL and Prisma

## What We're Building
Connecting our TikTok app to a real database so data doesn't disappear when we restart the server.

## Why Use a Database?
- **Permanent Storage**: Data stays even after server restarts
- **Better Performance**: Faster searches and data retrieval
- **User Management**: Secure login and user accounts
- **Data Relationships**: Connect users, videos, and comments properly

## Setup Process

### 1. Install PostgreSQL Database
```bash
sudo -u postgres psql
```

Create your database:
```sql
CREATE DATABASE tiktok_db;
CREATE USER tiktok_user WITH ENCRYPTED PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE tiktok_db TO tiktok_user;
```

### 2. Install Required Packages
```bash
npm install @prisma/client prisma bcrypt jsonwebtoken
```

### 3. Set Up Prisma
```bash
npx prisma init
```

This creates the files you need to connect to your database.

### 4. Configure Database Connection
Add to your `.env` file:
```
DATABASE_URL="postgresql://tiktok_user:your_password@localhost:5432/tiktok_db"
JWT_SECRET=your_secret_key
```

### 5. Create Database Tables
```bash
npx prisma migrate dev --name init
```

This creates all the tables your app needs (users, videos, comments, etc.).

## Key Features Added

### User Authentication
- **Secure Passwords**: Passwords are encrypted before storing
- **Login Tokens**: Users get a secure token when they login
- **Protected Routes**: Some features only work when logged in

### Database Operations
- **Create**: Add new users, videos, comments
- **Read**: Get data from database
- **Update**: Modify existing data
- **Delete**: Remove data when needed

### Data Relationships
- Users can have many videos
- Videos can have many comments
- Users can like videos and comments
- Users can follow other users

## Testing Your Setup

### 1. Start the Server
```bash
npm run dev
```

### 2. Test with Postman
1. Register a new user
2. Login with that user
3. Create a video (requires login)
4. Add comments to videos

### 3. Add Test Data
```bash
npm run seed
```

This adds sample users, videos, and comments to test with.

## File Structure
```
server/
├── prisma/
│   ├── schema.prisma      # Database structure
│   └── seed.js           # Test data
├── src/
│   ├── controllers/      # Business logic
│   ├── middleware/       # Authentication
│   └── lib/             # Database connection
└── .env                 # Configuration
```

## Important Concepts

### Database Tables
Think of tables like spreadsheets that store different types of data:
- **Users table**: Stores user information
- **Videos table**: Stores video information
- **Comments table**: Stores comments on videos

### Relationships
Tables can connect to each other:
- Each video belongs to one user
- Each comment belongs to one video
- Users can like many videos

### Security
- Passwords are encrypted (never stored as plain text)
- Login tokens expire after 30 days
- Some features require authentication

## Common Commands
```bash
# Start development server
npm run dev

# Create database changes
npx prisma migrate dev

# Add test data
npm run seed

# View database in browser
npx prisma studio
```

## Troubleshooting
- Make sure PostgreSQL is running
- Check your database connection string
- Verify environment variables are set correctly
- Run migrations if database structure changes

---
