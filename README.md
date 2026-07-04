# Graded Reader

A one-page web reader for personalized comprehensible-input graded readers
(built for Thai, where the word-spacing scaffolding matters). Stories are
written for you, on demand, by an AI tutor running in your own private
GitHub repo on your own Claude subscription — this page just renders them.

**Read it here: <https://cgaisl.github.io/elephant-stories/>**

## The reader

`index.html` is a single self-contained page, no build, no backend. It
renders stories live from any GitHub repo that has a `stories/` folder and a
`VOCABULARY.md` ledger. Features: story index, adjustable type size,
spaced/unspaced Thai toggle, per-story new-word chips, light/dark, and a
"request new story" button that opens a prefilled issue on your story repo.

Your repo name and (for private repos) a read-only token are stored in your
browser's localStorage only, and sent only to `api.github.com`.

Handy: `…/?repo=yourname/your-repo` prefills the repository on first visit —
bookmark it, or send it to a friend along with the template link below.

## Get your own stories

1. Go to the template repo —
   **<https://github.com/cgaisl/elephant-stories-template>** — and click
   **Use this template → Create a new repository**. Make it **private**
   (it will hold your learner profile).
2. Follow the template's `SETUP.md`: a read-only token for the reader, the
   Claude GitHub App, and a subscription token for the story-writing
   workflow. You need your own Claude Pro/Max subscription; ~10 minutes,
   one time.
3. Open the reader, point it at your repo (the ⚙ screen has a **Check
   setup** button that verifies the wiring), and open your first issue:
   tell the tutor your level and situation, and it sets up your learner
   profile and writes story ๑.

## How a story repo works

- `CLAUDE.md` — the tutoring method (static; the automation is forbidden
  from editing it, and a CI guard reverts violations).
- `PROFILE.md` — who you are as a learner: level, calibration, story-world
  cast, progression, durable preferences. The tutor updates it as you go
  and announces every change.
- `VOCABULARY.md` — the ledger of every word you know; the single source of
  truth that keeps stories ~90%+ comprehensible.
- `stories/` — your reading history, one markdown file per story.
- `.github/workflows/claude-story.yml` — turns a "new story" issue into a
  story: reads the method + your profile + your ledger, writes the next
  story, pushes it, and replies on the issue with the story and teaching
  notes.

Requests in plain language work: "beach theme", "zero new words today",
"harder", or from-now-on preferences ("~20 new words per story from now
on"), which get recorded in your profile.

## Hosting your own copy of the reader

Fork this repo, then Settings → Pages → Deploy from a branch → `main`,
root. The reader is then at `https://<you>.github.io/<repo>/`. It also
works opened as a local file.
