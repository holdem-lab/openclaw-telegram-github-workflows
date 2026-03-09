# GitHub -> Telegram workflow templates

These files are ready to copy into a repository:

- `.github/workflows/notify-telegram.yml` (reusable)
- `.github/workflows/telegram-notify.yml` (caller)

## Required GitHub Secrets

Add in each caller repository:

- `TELEGRAM_BOT_TOKEN`
- `TELEGRAM_CHAT_ID` (example: `-1001234567890`)

## Usage modes

- Central reusable workflow: keep `notify-telegram.yml` in one repo and use
  `OWNER/CENTRAL_REPO/.github/workflows/notify-telegram.yml@main`.
- Copy mode: copy `notify-telegram.yml` into each repo and set
  `uses: ./.github/workflows/notify-telegram.yml`.

## Mapping

- Issues: `opened` -> 🆕, `closed` -> ✅, `reopened` -> 🔄
- PRs: `opened` -> 🔀, `merged` -> 🟣, `closed` (not merged) -> ❌, `ready_for_review` -> 👀
- Other actions are skipped with success (`exit 0`).

## Telegram forum requirement

`topic_id` is required. Your target chat must be a forum-enabled supergroup.
