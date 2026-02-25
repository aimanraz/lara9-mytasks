# AGENTS.md

## Cursor Cloud specific instructions

This is a Laravel 9 CRUD Task Manager app (PHP 8.1, Blade/Bootstrap 4, Vite).

### System dependencies (pre-installed in snapshot)

- PHP 8.1 (via `ppa:ondrej/php`) with extensions: cli, mbstring, xml, curl, zip, bcmath, sqlite3, dom
- Composer 2.x at `/usr/local/bin/composer`

### Database

The dev environment uses **SQLite** (`DB_CONNECTION=sqlite`) instead of MySQL. The database file is at `database/database.sqlite`. No external DB service is needed.

### Key commands

| Action | Command |
|---|---|
| Install PHP deps | `composer install` |
| Install JS deps | `npm install` |
| Lint (code style) | `./vendor/bin/pint --test` |
| Fix lint | `./vendor/bin/pint` |
| Tests | `php artisan test` |
| Build assets | `npm run build` |
| Dev server | `php artisan serve --host=0.0.0.0 --port=8000` |
| Vite dev (HMR) | `npm run dev` |
| Migrations | `php artisan migrate` |

### Gotchas

- `.env` must exist before any artisan command. The update script handles this via `composer install` post-scripts, but if `.env` is missing, run: `cp .env.example .env && php artisan key:generate`.
- The `.env` is configured for SQLite. If you switch to MySQL, you must install and start MySQL and update `DB_CONNECTION`/`DB_DATABASE` accordingly.
- `./vendor/bin/pint --test` exits non-zero due to pre-existing style issues in the repo (5 files). This is not caused by agent changes.
- PHPUnit tests use the app's default DB connection. For isolated test runs, uncomment the SQLite `:memory:` lines in `phpunit.xml`.
