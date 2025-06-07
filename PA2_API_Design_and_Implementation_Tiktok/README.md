# TikTok API Project Reflection 🎥

## What I Built
A REST API for a TikTok-like app that handles videos, users, and comments. Users can upload videos, follow each other, like content, and leave comments - just like the real TikTok but as a backend service.

## Key Things I Learned

### 1. REST API Design Makes Sense
Before this project, APIs seemed confusing. But following REST principles made everything logical:
- GET for retrieving data
- POST for creating new stuff  
- PUT for updating existing items
- DELETE for removing things
- URLs that make sense like `/api/users/123/videos`

### 2. Planning Endpoints is Crucial
I learned to think about what actions users need before writing code:
- Users need to see videos → `GET /api/videos`
- Users want to follow others → `POST /api/users/:id/followers`
- Comments need likes too → `POST /api/comments/:id/likes`

This planning saved me from rewriting code later.

### 3. Data Relationships are Everywhere
Everything connects to everything:
- Videos belong to users
- Comments belong to videos
- Likes connect users to videos/comments
- Followers create user-to-user relationships

Managing these connections was harder than I expected.

## Biggest Challenges

### Organizing the Code
**Problem**: All my code was getting messy in one big file.
**Solution**: Split everything into separate files - controllers for logic, routes for endpoints, models for data. Much cleaner!

### Handling Different Data Types
**Problem**: Sometimes I needed user info, sometimes just user IDs, sometimes full video objects.
**Solution**: Created consistent response formats and decided what data each endpoint should return.

### Testing Everything
**Problem**: With so many endpoints, testing by hand took forever.
**Solution**: Used Postman to save requests and cURL commands to quickly test changes.

## What Worked Well

1. **Express.js** made creating endpoints really simple
2. **Consistent URL patterns** helped everything make sense
3. **JSON responses** worked perfectly with frontend apps
4. **Middleware setup** handled common tasks like CORS automatically

## What I'd Do Differently

1. **Add a real database** instead of storing everything in memory
2. **Implement user authentication** so people can't mess with others' content
3. **Add input validation** to prevent bad data from breaking things
4. **Write actual tests** instead of just manual testing
5. **Add error handling** for when things go wrong

## Main Takeaway
Building a REST API taught me that good planning beats good coding. Spending time thinking about what endpoints you need and how data connects saves hours of refactoring later.

The project also showed me how much work goes into making something that looks simple. TikTok's "just scroll and watch videos" experience requires tons of backend logic for users, videos, comments, and relationships between everything.

Most importantly, I learned that REST APIs are just a way to let different apps talk to each other in a predictable way - and once you understand the pattern, it becomes much easier to build and use them.