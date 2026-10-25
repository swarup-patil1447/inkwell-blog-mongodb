# InkWell — Module 03: Database Integration

This project extends the InkWell blog application with MongoDB database storage and an individual blog detail page.

## Technologies
- Frontend: HTML, CSS, JavaScript
- Backend: Node.js and Express.js
- Database: MongoDB Atlas with Mongoose
- Authentication: JWT
- Password storage: bcrypt password hashing

## Setup
1. Install Node.js 18 or newer.
2. Create a free MongoDB Atlas cluster: https://www.mongodb.com/atlas/database
3. In Atlas, create a database user and add your current IP address under Network Access.
4. Select **Connect → Drivers → Node.js** and copy the connection string.
5. In the project folder, install dependencies:
   ```bash
   npm install
   ```
6. Copy `.env.example` to `.env` (PowerShell: `Copy-Item .env.example .env`; Command Prompt: `copy .env.example .env`).
7. Edit `.env` and set `MONGODB_URI` to your real Atlas connection string. Set `JWT_SECRET` to a random secret of at least 32 characters. Do not commit `.env` to GitHub.
8. Start the application:
   ```bash
   npm start
   ```
9. Open http://localhost:3000. Check http://localhost:3000/api/health for `status: ok` and `database: connected`.

## API routes
| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/health` | Server and database health |
| POST | `/api/auth/register` | Register a user; password is hashed |
| POST | `/api/auth/login` | Log in and receive a JWT |
| GET | `/api/auth/me` | Get the logged-in user (token required) |
| GET | `/api/posts` | Retrieve all blog posts |
| GET | `/api/posts/mine` | Retrieve current user's posts (token required) |
| GET | `/api/posts/:id` | Retrieve an individual blog post |
| POST | `/api/posts` | Create a blog post (token required) |
| DELETE | `/api/posts/:id` | Delete your own post (token required) |

## Test checklist
- [ ] Configure MongoDB Atlas and `.env`.
- [ ] `npm install` completes successfully.
- [ ] Server starts and `/api/health` reports database connected.
- [ ] Register a user and log in.
- [ ] Create a blog post and see it on the homepage.
- [ ] Refresh and confirm the post remains in the database.
- [ ] Open a post's **Read story** link to see the individual details page.
- [ ] Verify dashboard and delete functionality.
- [ ] Push to GitHub without `.env` or `node_modules`.
- [ ] Share the repository on LinkedIn.

## GitHub details
Suggested repository: `inkwell-blog-application`

Description: A responsive blog application built with HTML, CSS, JavaScript, Node.js, Express.js, and MongoDB. Features REST APIs, JWT authentication, secure password hashing, database integration, and individual blog post pages.

## Security note
This is an educational project. JWT is stored in browser localStorage in the supplied frontend for simplicity. A production application should consider secure HTTP-only cookies, HTTPS, rate limiting, robust validation, and database backups.
