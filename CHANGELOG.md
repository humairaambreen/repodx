# Changelog

## 0.5.0

The first release built mostly by the community. Thank you to everyone who contributed!

- New secret providers:
  - OpenRouter (#53, @HerculesNode)
  - npm (#45, @hy3560)
  - PyPI (#73, @skyqueenn)
  - GitLab (#62, @0xskyeagle)
  - DigitalOcean (#60, @0xskyking)
  - Shopify (#59, @QavurDagli)
  - Perplexity (#43, @sametderdi462-alt)
  - Replicate (#47, @ahmetmizrap1232-sys)
  - Discord webhook URLs (#50, @subathusniye-byte)
  - Slack webhook URLs (#49, @will-codes-afk; #51, @kriptodenemeleri3-dotcom)
- Secrets behind public env prefixes such as `NEXT_PUBLIC_OPENAI_API_KEY` or `VITE_STRIPE_SECRET_KEY` are reported, even when the value is empty, because the framework ships them to the browser (#29, @amandeavor). Provider keys behind a public prefix are critical, findings in test and example folders are one level lower, and the check is faster (#61, @bernalalexis-try).
- `repodx --quiet` prints a single score line for scripts and hooks (#44, #46, @HarshRajSinghania).
- Colored output works in Windows terminals (#52, @aplatogg).
- Database URLs with percent-encoded passwords (`p%40ss`) are now detected (#55, @aplatogg).

Thanks to @HerculesNode, @hy3560, @skyqueenn, @0xskyeagle, @0xskyking, @QavurDagli, @sametderdi462-alt, @ahmetmizrap1232-sys, @subathusniye-byte, @will-codes-afk, @kriptodenemeleri3-dotcom, @amandeavor, @bernalalexis-try, @HarshRajSinghania and @aplatogg.

## 0.4.0

- `repodx --fix` adds missing `.gitignore` lines and creates a `.env.example` with empty values, then scans again and shows the new score. It never deletes files or edits code, and running it twice changes nothing.
- `repodx --prompt` prints a ready-to-paste prompt for AI coding tools with every finding, its location and its fix, and rules against leaking secret values.
- `repodx --install-hook` installs a Git pre-commit hook that blocks commits with critical findings. It doesn't overwrite existing hooks it didn't install.
- PyPI page shows the author and links to issues and the changelog.

## 0.3.2

- Releases are now published to PyPI automatically by the release workflow (trusted publishing, no API tokens).
- A test keeps the version in `repodx.py`, `pyproject.toml`, `CHANGELOG.md` and the README install examples in sync.

## 0.3.1

- Published on PyPI: `pipx install repodx`

## 0.3.0

- Tested against eight large public repositories. Critical false alarms went from 136 to 0; the one remaining critical finding is real.
- Skip documentation placeholders (`...EXAMPLE`, `[YOUR-PASSWORD]`, `xoxb-0000...`, templated hosts) and the local Supabase CLI demo keys.
- Private keys are only reported when a real key body follows the header.
- Secrets and `.env` files in test and example folders are warnings.
- `.env` files that only contain public variables (`NEXT_PUBLIC_`, `VITE_`, ...) are warnings.
- Firebase rules: public writes are critical, public reads are info.
- `.gitignore` expectations follow the project type, and globs such as `.env*` count.
- `dist/` of a JavaScript GitHub Action is not junk.
- README "Quickstart", "Getting started" and "Running locally" sections count as Installation and Usage.
- Each kind of problem counts at most three times toward the score.
- About 3x faster on large repositories.

## 0.2.0

- Secret scanning, Supabase and Firebase checks, `.env` files, large files, LICENSE, `.env.example`, agent files.
- Score and grade, `--json`, `--format markdown`, `--badge`, `--fail-on`.
- `.repodxignore`, `repodx:ignore`, GitHub Action, pre-commit hook, `pyproject.toml`.

## 0.1.0

- Junk files, `.gitignore` and README checks.
