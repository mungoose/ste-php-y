# Progress

## Decisions
- Repo: `ste-php-y`, public on GitHub (account `mungoose`). CLAUDE.md and PROGRESS.md are committed.
- PHP runs only inside Sail (Docker via OrbStack). No PHP or Composer on the Mac.
- Versions checked 2026-11-09: Laravel 13.40 (needs PHP ^8.3), Lighthouse 6.74 (supports Laravel 9–13).

## Current milestone
**0. Setup**: new Laravel app with Sail and MySQL, git repo on GitHub, default tests pass.

## Done
- Step 0.1: Laravel 13 app via the Sail installer, PHP 8.5 runtime, MySQL 8.4, PHPUnit. Generated into a nested folder and moved up; installer's CLAUDE.md/AGENTS.md dropped. Default tests pass, migrations ran on MySQL.

## Next
- Step 0.2: git init, first commit, public GitHub repo `ste-php-y`, push.

## Areas covered
- [ ] Project structure, `.env` and config, Artisan
- [ ] Migrations and the schema builder
- [ ] Eloquent models, relationships, casts (including an enum cast)
- [ ] Factories and seeders
- [ ] A plain PHP class for business logic, injected through the service container
- [ ] Validation
- [ ] Authentication with Sanctum tokens
- [ ] GraphQL with Lighthouse: schema, queries, a mutation, directives
- [ ] Database transaction and row locking
- [ ] Feature tests
- [ ] GitHub Actions CI

## Struggled with
- OrbStack via Homebrew only installs the app; the docker CLI appears after first launch.
- `sail` is `./vendor/bin/sail` (project-local, like node_modules/.bin), and `artisan` needs PHP, so it only runs via `sail artisan`.

## Later
- README (milestone 4): fresh-clone setup steps: copy `.env.example` → `.env` before the first `sail up`, Composer install through a throwaway `laravelsail/php85-composer` container, `sail artisan key:generate`, `sail artisan migrate`.
