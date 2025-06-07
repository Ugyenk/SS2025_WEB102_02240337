# My API Project - What I Learned

## What I Built
I made a REST API for a social media platform like Instagram. Users can create accounts, share posts, leave comments, like content, and follow each other.

## Key Lessons

**Good design comes first** - I learned that planning your API structure before coding saves tons of time later. Figuring out what endpoints you need and how they connect is crucial.

**REST patterns make sense** - Once I understood the basic rules (GET to fetch, POST to create, PUT to update, DELETE to remove), everything became logical and predictable.

**Error handling matters** - Users need clear messages when things go wrong. Generic errors are frustrating, but specific helpful errors make the API much better to use.

**Everything needs to connect** - Users create posts, posts have comments, people follow each other. Managing all these relationships was harder than I expected.

## Biggest Challenges

**Making URLs consistent** - I struggled with patterns like "should comments be at `/posts/1/comments` or `/comments?post_id=1`?" I settled on using query parameters for filtering to keep things simple.

**Supporting different formats** - Some users wanted JSON, others wanted XML or HTML. I built middleware that checks what format they want and responds accordingly.

**Catching errors properly** - In Node.js, errors in async code don't get caught automatically. I had to create special wrapper functions to handle this.

**Creating realistic test data** - I needed fake users, posts, comments, and likes that all connected properly. This took more planning than expected.

## What Went Well
- Express.js made building endpoints straightforward
- Following REST patterns kept everything organized
- Adding proper status codes made the API feel professional
- Creating documentation helped me think through the design

## What I'd Improve
- Connect to a real database instead of fake data
- Add user login and authentication
- Write automated tests instead of manual testing
- Add limits to prevent people from spamming the API
- Better validation to catch bad input

## Main Takeaway
This project taught me that **good APIs are designed, not just coded**. Taking time to plan the structure, think about the user experience, and handle errors properly creates something that's actually useful and maintainable.

The biggest lesson: consistency is everything. When your API follows predictable patterns, it becomes much easier for developers to understand and use.