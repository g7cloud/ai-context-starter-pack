# AI context starter pack

A ready-made way for a project to remember things between AI sessions, so you never have to manage context by
hand. Copy it into a project and your AI assistant will read what the project already knows before it starts,
and write down what it learned when it finishes.

It is plain markdown files. There is nothing to install and nothing to run. It works for software, product
work, content, operations, or anything else you do with an AI assistant in a folder of files.

## Start in three steps

1. **Copy** `AGENTS.md`, `CLAUDE.md` and the `context/` folder into the top of your project (or use this
   repository as a template for a new one).
2. **Open your AI assistant** in the project and say: **"Set up the context for this project."** It reads what
   is there, asks you up to five questions and fills in the map.
3. **Work as usual.** At the end of each task the assistant tells you in a line or two what it noted in `context/`.

If your project already has a `CLAUDE.md` or `AGENTS.md`, do not overwrite it. Copy `context/` in, then ask
the assistant to "bring our existing instructions and documents into the context tree".

## What you get

```
AGENTS.md                  the instructions every AI tool reads at the start of a session
CLAUDE.md                  one line that points Claude at AGENTS.md
context/
  README.md                the map: what the project is, its rules, its topics
  now.md                   where the work stands: in progress, next, blocked, open questions
  setup.md                 first setup, and bringing in what the project already has
  how-this-works.md        the full rules for keeping the tree (the assistant opens it when needed)
  learnings/               short lessons and corrections, read every session
  history/                 dated records: what went wrong, what was decided, what changed
  plans/                   proposals that are not done yet
  templates/               a skeleton for each kind of file
```

Topics get added as the project needs them. A topic is a folder with its own `README.md` that says what is
inside and where to start:

| An engineering project | A product team | A content team |
|---|---|---|
| `context/api/` | `context/customers/` | `context/tone-of-voice/` |
| `context/billing/` | `context/pricing/` | `context/blog/` |
| `context/deploy/` | `context/roadmap/` | `context/newsletter/` |
| `context/api/history/` | `context/pricing/history/` | `context/blog/plans/` |

## How it works

- **Read top down.** The assistant reads the map, then one topic's `README.md`, then the one document the task
  needs. It never loads everything, so it stays quick and cheap however much the project knows.
- **Every `README.md` is a router.** It says what its folder holds and what to open next. It never repeats what
  the documents say.
- **Small files.** One question per document, 20,000 characters at most. A document that grows past that is
  split into a folder of smaller ones.
- **One home for each fact.** The assistant updates the document that exists and links to it from elsewhere.
- **Written as it goes.** Decisions, findings and where the work stands are saved when they happen, so a
  session that is cut off loses little. Anything you asked for that will be used again is saved as a document.
- **Nothing true is deleted.** What stops being true moves to `history/` or is marked as replaced.
- **No secrets.** Passwords and keys are never written down, only where they are kept.

## Things to say to your assistant

| Say | What happens |
|---|---|
| "Set up the context for this project." | It fills in the map and writes the first documents. |
| "Where are we?" or "Carry on." | It reads `now.md` and picks up where the last session stopped. |
| "Research … and save what you find." | It writes a findings document: each finding with its source, date and how sure we are. |
| "Remember that …" | It adds a line to the learnings list that every later session reads. |
| "From now on, never …" | It adds a rule to the map, with the reason. |
| "Write up what just went wrong." | It writes a dated record in `history/`, and changes the rule or routine if there is a lesson. |
| "Write this up as a plan." | It writes a proposal in `plans/`, kept apart from how things are now. |
| "Check the context." | It looks for files that are too big, broken links, stale documents and duplicates. |
| "Bring our existing documents into the context tree." | It moves what you already have into the tree, checked as it goes. |

## Which tools read it

- **Claude Code** reads `CLAUDE.md`, which loads `AGENTS.md`.
- **Tools that read `AGENTS.md`** (Codex, Cursor, GitHub Copilot and others) need nothing else.
- **A tool that reads a different file:** make that file one line that says to read `AGENTS.md` first.
- **A chat assistant with no access to your files:** add `AGENTS.md` and the `context/` files to the project's
  knowledge. It can read them, and it will give you any updates as text to save yourself.

## Good to know

- These are instructions, not enforcement. An assistant follows them well, but it can still miss a step, so
  read what it writes into `context/` as you would any other change, and review it with the work it describes.
- Keep `context/` with the project and under version control, so it has a history and everyone gets the same
  copy.
- To change how the tree is kept for your team, edit `AGENTS.md` (short, loaded every session) and
  `context/how-this-works.md` (the detail). Keep `AGENTS.md` under 6,000 characters.
