# My Social Media API Project - What I Learned

## What I Built
I created a REST API for a social media app like Instagram. Users can create accounts, post photos, comment, like posts, and follow each other - all through backend endpoints.

## Key Lessons

**REST makes sense** - Once I understood the pattern (GET to fetch, POST to create, PUT to update, DELETE to remove), building endpoints became logical.

**Planning saves time** - I mapped out what users needed to do before coding. Things like "users need to see posts" became `GET /posts` and "users want to follow others" became `POST /followers`.

**Everything connects** - Users have posts, posts have comments, people follow each other. Managing all these relationships was the hardest part.

## Biggest Challenges

**Organizing code** - I started with everything in one file. Breaking it into controllers, routes, and middleware made it much cleaner and easier to work with.

**Different response formats** - Users wanted JSON, XML, or HTML responses. Learning content negotiation helped me handle this automatically.

**Error handling** - When things went wrong, I needed consistent error messages. Building proper error handling middleware solved this.

## What Went Well
- Express.js made creating endpoints simple
- Mock data helped me test without a real database
- Following REST patterns kept everything organized
- Adding proper HTTP status codes made the API professional

## What I'd Improve
- Add real user authentication instead of mock data
- Connect to a proper database
- Write automated tests instead of manual testing
- Add rate limiting to prevent spam
- Better input validation to catch bad data

## Main Takeaway
Building a REST API taught me that good structure beats clever code. When you follow standard patterns like REST, everything becomes predictable and easier to maintain.

This project showed me how much work goes into making simple features work. A basic "like a post" button requires user authentication, database updates, and proper error handling behind the scenes.