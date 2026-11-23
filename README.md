# career-agent-skills

A collection of reusable AI skills for job searching, CV optimization, career development, job applications, and professional growth.

Each skill is a set of instructions you give your own AI assistant (ChatGPT, Claude, Gemini or any other) so it does one career task well. Jobak's AI tools offer them under **Use in your own AI**, with a version picker.

## Skills

| Skill | What it does | Latest |
|---|---|---|
| [`cover-letter`](cover-letter/) | Analyses your CV and a job posting, flags text planted for AI tools, and writes a personalised cover letter. | [1.0.0](cover-letter/versions/1.0.0/SKILL.md) |
| [`cv-review`](cv-review/) | Scores your CV the way recruiters and ATS software read it, explains what to fix, and improves it with you without inventing anything. | [1.0.0](cv-review/versions/1.0.0/SKILL.md) |

## Using a skill

1. Open the skill's latest `versions/<x.y.z>/SKILL.md` and copy it (or download the file).
2. Paste it into your AI assistant as your first message.
3. Give it what it asks for: your CV, a job posting if the skill uses one, and anything else.

## Layout

```
<skill>/
├── skill.json              title, description, latest, and every version with its date and notes
└── versions/
    ├── 1.0.0/SKILL.md
    └── 1.1.0/SKILL.md
```

`skill.json`:

```json
{
  "name": "cover-letter",
  "title": "Cover letter",
  "description": "One sentence on what it does.",
  "latest": "1.0.0",
  "versions": [
    { "version": "1.0.0", "date": "2026-11-22", "notes": "One line on what changed." }
  ]
}
```

## Releasing a new version

1. Copy the latest `versions/<x.y.z>/` folder to the new version number and edit its `SKILL.md`. **Never edit a released version**: people may be using it, and Jobak caches each version as unchanging.
2. Add an entry to `versions` in `skill.json` (`version`, `date` as `YYYY-MM-DD`, one line of `notes`) and point `latest` at it.
3. Choose the number by what changed (semantic versioning):
   - **patch** (1.0.1): wording fixes, same behaviour;
   - **minor** (1.1.0): new steps or rules that keep the same flow for the user;
   - **major** (2.0.0): a different flow, or one that asks the user for different things.

The order of `versions` doesn't matter. Only versions listed in `skill.json` are offered, so an unlisted folder (a draft) stays out of Jobak. A listed version without its `SKILL.md` is an error.

## How Jobak reads this repository

Jobak fetches `skill.json` and each `SKILL.md` from this repository's `main` branch (`raw.githubusercontent.com`). It caches a version's content for good and re-reads `skill.json` every few minutes, so a new release shows up in Jobak within minutes of being pushed. GitHub's own CDN can add a few more.

## License

[MIT](LICENSE)
