# Progress

## Decisions
- Repo: `ste-php-y`, public on GitHub (account `mungoose`). CLAUDE.md and PROGRESS.md are committed.
- App and MySQL run in Sail (Docker via OrbStack). PHP 8.5 + Composer also on the Mac (Homebrew), added after Sail-only proved awkward for a breadth-first project. artisan/tests still via `sail` (DB_HOST=mysql).
- Versions checked 2026-11-09: Laravel 13.40 (needs PHP ^8.3), Lighthouse 6.74 (supports Laravel 9–13).

## Current milestone
**1. Data model**: migrations, models, relationships, the status enum, factories, one seeder. Done when `sail artisan migrate:fresh --seed` gives realistic data and is queryable in Tinker.

## Done
- Step 0.1: Laravel 13 app via the Sail installer, PHP 8.5 runtime, MySQL 8.4, PHPUnit. Generated into a nested folder and moved up; installer's CLAUDE.md/AGENTS.md dropped. Default tests pass, migrations ran on MySQL.
- Step 0.2: git repo, pushed to https://github.com/mungoose/ste-php-y (public, branch `master`). First commit subject isn't Conventional Commits; left as is unless Margus amends it.
- Milestone 0 done (2026-11-10).

## Next
- Answer the milestone 0 questions, then step 1.1: design the schema (tables, columns, types, foreign keys) on paper before writing migrations.

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
- Milestone 0 questions: thought Sail mirrors production (it's a dev image, not prod); thought PHP minor versions don't break things and that compose.yaml sets the CI/prod PHP version (it's dev only; `composer.json` `require.php` / `config.platform.php`, CI and the prod image do). APP_KEY answer was mostly good; missed encrypted data loss and `APP_PREVIOUS_KEYS`.
- `sail` is `./vendor/bin/sail` (project-local, like node_modules/.bin), and `artisan` needs PHP, so it only runs via `sail artisan`.

## Later
- README (milestone 4): fresh-clone setup steps: copy `.env.example` → `.env` before the first `sail up`, Composer install through a throwaway `laravelsail/php85-composer` container, `sail artisan key:generate`, `sail artisan migrate`.
