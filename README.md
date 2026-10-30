# StudyFlow - Student Task Manager

A lightweight Flask website for CCEN 448 Lab Exercise 6. Includes account registration, login/logout, password hashing, and per-user tasks stored in SQLite.

## Run locally (macOS/Linux)

```bash
cd student-task-manager
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export SECRET_KEY="$(python3 -c 'import secrets; print(secrets.token_hex(32))')"
python app.py
```

Open http://127.0.0.1:5000. Create an account, add a task, mark it done, and delete it.

## Run on Ubuntu Lightsail

Place the project in `/opt/website`, install Python 3, venv, and pip, and run:

```bash
cd /opt/website
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
export SECRET_KEY="$(python3 -c 'import secrets; print(secrets.token_hex(32))')"
.venv/bin/gunicorn -w 2 -b 0.0.0.0:5000 app:app
```

Use a persistent `SECRET_KEY` in a protected environment file for production; do not regenerate it on every restart. SQLite database defaults to `/opt/website/tasks.db` on Lightsail. Ensure the app process has write permissions. For a real public deployment, use HTTPS, a dedicated service user, a reverse proxy, CSRF protection, rate limiting, and a robust production database. This is a classroom demonstration app.

## Task 2 screenshot

Open `app.py` and `templates/dashboard.html` in your code editor, with the folder tree visible. Capture the editor showing the authentication routes and database model. Do not screenshot secrets.
