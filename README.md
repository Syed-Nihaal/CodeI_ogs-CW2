# CodeLogs

CodeLogs is a full-stack web application designed for developers to create, share, and explore technical blog posts with syntax-highlighted code snippets. It features a single-page interface with a Node.js/Express backend, MongoDB for data persistence, and AJAX for seamless interactions. Advanced features include a user following system, personalised feeds, comments, likes, file attachments, real-time search, and integration with third-party services like GitHub Gists and DEV.to.

## Tech Stack

- Node.js (ES modules)
- Express
- MongoDB
- Express Session
- Multer (file uploads)

## Prerequisites

Make sure these are installed and running:

1. Node.js 20+
2. MongoDB Community Server (local instance on `mongodb://localhost:27017`)
3. npm

## Project Structure

- `server.js`: Main Express server and API routes
- `setup_db.js`: Creates indexes and prepares DB collections
- `connect_db.js`: MongoDB connection helper
- `public/`: Frontend files (HTML/CSS/JS and uploads)
- `db_dump/`: MongoDB dump files

## Installation

From the project root:

```bash
npm install
```

## Database Setup

### Option A: Automatic setup (recommended)

This runs index creation and migration logic:

```bash
npm run setup_db
```

### Option B: Restore provided dump data

If you want to load the provided dataset from `db_dump/codelogs_db`, run:

```bash
mongorestore --db codelogs_db ./db_dump/codelogs_db
```

If your local MongoDB tools are not on PATH, use the full path to `mongorestore.exe`.

## Run the App

Use the start script:

```bash
npm start
```

This command does two things:

1. Runs `setup_db.js`
2. Starts `server.js`

Server default: `http://localhost:8080`

## App URL

The app is served under a student path prefix:

- Main app: `http://localhost:8080/M01039337/`
- Health/test route: `http://localhost:8080/M01039337/test`

Root (`/`) redirects to the student path automatically.

## Useful Scripts

- `npm start`: setup DB and start server
- `npm run setup_db`: setup indexes/migrations only

## File Upload Notes

- Upload destination: `public/assets/uploads/`
- Maximum file size: 5 MB
- Allowed extensions/types include: `jpeg`, `jpg`, `png`, `gif`, `pdf`, `txt`, `doc`, `docx`, `zip`

## Troubleshooting

### MongoDB connection fails

- Check MongoDB is running on `localhost:27017`
- Verify no firewall/service restrictions are blocking local connections

### Port already in use

- Change `PORT` in `server.js` or stop the process currently using `8080`

### `mongorestore` not found

- Install MongoDB Database Tools
- Add the tools folder to your PATH

## Notes

- This project currently has no automated tests configured (`npm test` is a placeholder).
- Session secret is hardcoded in `server.js`; replace it with an environment variable for production use.
