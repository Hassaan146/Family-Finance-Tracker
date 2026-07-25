# Family Finance Tracker

A Django web app that moves family expense tracking from traditional diaries to the web. One person creates a family, everyone else joins it with a short code, and all members log expenses into a shared ledger.

## How it works

1. **Register / log in** — accounts use a custom user model (`User_a`, extending `AbstractUser`).
2. **Create a family** — the creator becomes the owner and gets a 6-character **joining ID**.
3. **Join a family** — other members enter the joining ID to be added to the same family.
4. **Track expenses** — each expense records its name, amount, date, and *which member spent it*, scoped to the family.

## Data model

- **`Family`** — family name plus per-member details (name, age, gender), owner flag, and the 6-char `joining_id`
- **`User_a`** — custom auth user with a `has_joined` flag and a link to their family
- **`Expenses`** — name, amount, auto-dated, linked to the family and the member who spent it

## Tech stack

- **Django** (single `home` app, project config in `core/`)
- **SQLite** for storage
- Server-rendered templates: register, login, create family, join family, family dashboard, expenses

## Running locally

```bash
pip install django
python manage.py migrate
python manage.py runserver
```

Then open `http://127.0.0.1:8000/`.

> An earlier iteration of this project lives at [Family-Expense-Tracker](https://github.com/Hassaan146/Family-Expense-Tracker).
