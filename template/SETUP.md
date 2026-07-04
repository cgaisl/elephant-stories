# Setting up your story repo

You've copied the template into your own **private** GitHub repo. Three
one-time steps and you're reading.

## 0. Prerequisites

- A GitHub account (free is fine).
- A Claude Pro or Max subscription — the story-writing workflow runs on
  *your* subscription via an OAuth token; there is no shared backend.
- [Claude Code](https://claude.com/claude-code) installed locally (only
  needed once, to mint the token).

## 1. Reader access token

The reader web page needs read access to this private repo:

1. GitHub → Settings → Developer settings → Fine-grained personal access
   tokens → *Generate new token*
2. Repository access: **Only select repositories** → this repo
3. Repository permissions: **Contents → Read-only** (nothing else)
4. Open the reader page, enter `yourname/your-repo` and paste the token.
   Both are stored only in your browser.

## 2. Claude GitHub App

In a local Claude Code terminal run `/install-github-app`, or install
manually at <https://github.com/apps/claude>, and grant it this repo.

## 3. Subscription token for the workflow

```sh
claude setup-token
```

Copy the token it prints, then: repo → Settings → Secrets and variables →
Actions → *New repository secret* → name `CLAUDE_CODE_OAUTH_TOKEN`, value =
the token.

## 4. Onboard yourself

Open an issue on this repo (or use the reader's request button) mentioning
`@claude`, and introduce yourself: your level, whether you can read the
script yet, where you live, what you want from the stories. The tutor fills
in `PROFILE.md`, seeds the vocabulary ledger, and writes your first story as
an issue comment. From then on, every request is just an issue away.

Note on usage accounting: automated runs may draw from a separate monthly
credit pool included with your subscription rather than interactive session
limits — check <https://platform.claude.com/settings/usage> if curious.
