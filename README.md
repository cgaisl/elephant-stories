# Graded Reader

A one-page web reader for personalized comprehensible-input graded readers
(built for Thai, where the word-spacing scaffolding matters), plus a template
for running your own AI-tutored story repo.

**Reader** (`index.html`): renders stories live from any GitHub repo that has a
`stories/` folder and a `VOCABULARY.md` ledger. Story index, adjustable type
size, spaced/unspaced toggle, per-story new-word chips, light/dark, and a
"request new story" button that opens a prefilled issue on your story repo.
Your repo name and (for private repos) a read-only token are stored in your
browser's localStorage only — this page has no backend and talks only to
`api.github.com`.

## Hosting the reader (GitHub Pages)

This repo is meant to be published with GitHub Pages: Settings → Pages →
Deploy from a branch → `main`, root. The reader is then at
`https://<owner>.github.io/<repo>/`. It also works opened as a local file.

## Getting your own stories

1. Create a **private** repo for your stories and copy the contents of
   [`template/`](template/) into it.
2. Follow the template's `SETUP.md` (three one-time steps: a read token for
   the reader, the Claude GitHub App, and a Claude subscription token for the
   story-writing workflow — you need your own Claude Pro/Max subscription).
3. Open the reader, point it at your repo, and open your first issue: tell
   the tutor your level and situation, and it sets up your learner profile
   and writes story ๑.

## How a story repo works

- `CLAUDE.md` — the tutoring method (static; the automation is forbidden from
  editing it, and a CI guard reverts violations).
- `PROFILE.md` — who you are as a learner: level, calibration, story-world
  cast, progression, durable preferences. The tutor updates it as you go and
  announces every change.
- `VOCABULARY.md` — the ledger of every word you know; the single source of
  truth that keeps stories ~90%+ comprehensible.
- `stories/` — your reading history, one markdown file per story.
- `.github/workflows/claude-story.yml` — turns a "new story" issue into a
  story: reads the method + your profile + your ledger, writes the next
  story, pushes it, and replies on the issue with the story and teaching
  notes.

Requests in plain language work: "beach theme", "zero new words today",
"harder", or from-now-on preferences ("~20 new words per story from now on"),
which get recorded in your profile.
