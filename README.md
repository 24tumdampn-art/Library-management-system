# Library Management System

A library management application built with HTML, CSS, JavaScript, Python Flask, and SQLite.

## Features

- Add, search, filter, and delete books.
- Register members and view their borrowed-book counts.
- Issue books to members and record returns.
- View totals for books, available books, issued books, and members.
- Prevent duplicate ISBNs and deletion of issued books.

## Requirements

- Python 3.9 or newer
- Node.js 18 or newer, including npm
- Git (to clone this repository)

## First-time setup on Windows

Open PowerShell and run:

```powershell
git clone https://github.com/Shriyansh06/Library-management-system.git
cd Library-management-system
py -3 -m venv backend/venv
.\backend\venv\Scripts\python.exe -m pip install -r backend/requirements.txt
npm.cmd install
npm.cmd start
```

If `py` is unavailable, use the full path to your installed Python executable to create the environment:

```powershell
& 'C:\path\to\python.exe' -m venv backend/venv
```

Open **http://127.0.0.1:3000** in your browser. Keep the terminal running while using the app. Press **Ctrl+C** to stop it.

## Run it again

No reinstallation or virtual-environment activation is needed. Open PowerShell in your project folder and run:

```powershell
npm.cmd start
```

For the original local project stored in `E:\lib2`:

```powershell
cd E:\lib2
npm.cmd start
```

This single command starts both the webpage and the API.

## First-time setup on macOS or Linux

```bash
git clone https://github.com/Shriyansh06/Library-management-system.git
cd Library-management-system
python3 -m venv backend/venv
backend/venv/bin/python -m pip install -r backend/requirements.txt
npm install
npm start
```

For subsequent runs, enter the project folder and run `npm start`.

## Tests

```powershell
npm.cmd test
```

On macOS or Linux, use `npm test`. The suite checks book and member workflows, invalid input, frontend serving, and database initialization. Tests use a temporary database and leave your library records unchanged.

## Project structure

```text
backend/
  app.py             Flask routes and web server
  database.py        SQLite schema and initial demo records
  requirements.txt   Python dependencies
  test_api.py        API and regression tests
frontend/
  index.html         Dashboard and forms
  style.css          Styles
  app.js             Browser interactions and API requests
scripts/
  start.cjs          Cross-platform startup and test launcher
package.json         npm commands
package-lock.json    Node dependency lockfile
```

The `database/library.db` file is created automatically on first launch. Local database records, Python environments, and installed Node dependencies are excluded from version control. Back up your local database separately if you need to preserve your records.

## API endpoints

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/` | Dashboard |
| GET | `/api/health` | Server health |
| GET | `/api/books` | List books |
| POST | `/api/books` | Add a book |
| GET | `/api/books/search?q=term` | Search by title, author, or ISBN |
| POST | `/api/books/<id>/issue` | Issue a book using a `member_id` |
| POST | `/api/books/<id>/return` | Return a book |
| DELETE | `/api/books/<id>` | Delete an available book |
| GET | `/api/members` | List members |
| POST | `/api/members` | Register a member |

## Troubleshooting

- **Python with Flask is required:** Complete the Python environment and dependency installation steps above. The launcher detects `backend/venv` automatically. You can also set `PYTHON` to a Python executable with the dependencies installed.
- **Port already in use:** Stop your previous server with Ctrl+C, or select another port in PowerShell:

  ```powershell
  $env:PORT = '3001'
  npm.cmd start
  ```

  Then open http://127.0.0.1:3001.

- **Cannot connect:** Keep the startup terminal open and use the printed HTTP address. Avoid opening `index.html` directly.
- **Run without npm:** Use `.\backend\venv\Scripts\python.exe backend/app.py` on Windows or `backend/venv/bin/python backend/app.py` on macOS/Linux. Direct Python startup defaults to http://127.0.0.1:5000.

The included Flask server is intended for local development.
