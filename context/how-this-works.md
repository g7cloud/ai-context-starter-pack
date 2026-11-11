---
summary: "How the context tree is organised and kept: the kinds of file and their limits, what a README routes, splitting, naming, first setup, bringing in existing documents, the edge cases, working with other people, and a health check."
status: current
updated: 2026-11-11
---
# How this context tree works

Context is one tree, read top down: a small map that is always read, a `README.md` for each folder that says
what to open next, then one document opened on purpose. Every read is small. `AGENTS.md` holds the short version
that every session loads; this is the detail. Up: [the map](README.md).

```
AGENTS.md                      how to work here: loaded by every AI tool, every session
context/README.md              the map: what the project is, its rules, its topics
context/<topic>/README.md      a topic's router: what it holds, the traps, where to start
context/<topic>/<doc>.md       one question per document, in the deepest folder that fits
context/<…>/history/           dated records: incidents, decisions, changes
context/<…>/plans/             proposals, until they are done
context/learnings/             lessons, one line each in its README; a file for one that needs explaining
context/templates/             a skeleton for each kind of file
```

## The kinds of file

| Kind | What it is | Limit | Template |
|---|---|---|---|
| Map | `context/README.md`. What the project is, its rules, its topics. | 20,000 characters | it is its own |
| Router | A topic's `README.md`. What the folder holds and where to start. | 20,000 | `topic-router.md` |
| Document | One question, answered as things are now. | 20,000 | `document.md` |
| Record | Something that happened, with its date. Not rewritten later. | 20,000 | `record.md` |
| Plan | Something proposed and not yet done. | 20,000 | `plan.md` |
| Learnings list | `learnings/README.md`. Read every session. One dated line per lesson. | 40 lines | it is its own |
| Learning file | Only for a lesson that needs more than its line. | about 1,500 | `learning.md` |
| `AGENTS.md` | Loaded in full every session, so it stays small. | 6,000 | none |

Most documents are far shorter than their limit. The limit is where you stop and split.

**A rule or a learning?** A rule is something that must never be broken, or that the person states as one
("never", "always", "from now on"). It goes in the map with its reason, where every session reads it as
binding. Everything else that is worth remembering is a learning.

## The top of every file

```
---
summary: "<The answer in one or two sentences. It is what a reader sees when searching.>"
status: current
updated: YYYY-MM-DD
---
```

- `status`: `current` (how things are), `proposal` (a plan), `historical` (true when written), `superseded`
  (add `superseded_by: <path>`). A record is `historical` from the start.
- `updated`: the day the content last changed. Add `verified: YYYY-MM-DD` only when you checked the document
  against the real thing yourself that day. Being told is not checking. If you could not check something, say
  so in the document.

## What a README routes

- **A router routes. It never restates.** It says what the folder holds, its rules and traps, and where to start
  for each common task. Its line for a document names the question that document answers, in words that stay
  true when the detail changes. Figures, status and ticket numbers live in the document only.
- **Whoever adds a document adds its line** to the `README.md` above it. A reader who needs a third document to
  answer one question means a router is missing a pointer: add it.
- **Past about 25 documents in one folder**, group them into subfolders, each with its own `README.md`.
- **`history/` and `plans/` keep no list.** The file names (date and subject) are the index.
- **Every document stands alone.** A reader may arrive from a search, so the summary says what it answers, the
  first paragraph gives the answer, and it links up to its router.

## Splitting a document that is too big

Split by meaning, never by size. No `-part-2`.

1. List the questions a reader would bring to it. Each becomes a child document.
2. Make a folder named after the document, with one child for each question.
3. Turn the original into that folder's `README.md` (move it, and fix the links that pointed at it).
4. Move what is not current: a "what we will do" section goes to `plans/`, a dated story goes to `history/`.
5. Check: every child is under the limit, nothing was lost, and no fact now sits in two places.

A log that keeps growing (decisions, gotchas, changes) becomes a folder of records, one file each.

## Names

- Folders and files: lowercase words joined by hyphens, named for what they are (`pricing`, `release-process`,
  `tone-of-voice`). Never for a team, a person or a ticket.
- Only records carry a date: `YYYY-MM-DD-<what-happened>.md`, so a folder lists in date order.
- A topic is a part of the work people deal with as a unit: a feature, a service, a channel, a customer group,
  a process.

## First setup

When the map still has `<placeholders>`:

1. Look at what is already here: the files, any README or documents, recent history. Do not ask for what you
   can read.
2. Ask the person at most five short questions for what you cannot: what this is and who it is for, its state
   and owner, the rules that must never be broken, where the real thing lives, and what an AI keeps getting
   wrong here (for writing work: how it should sound, with an example they like).
3. Fill in the map and the learnings list. Delete the sections and placeholder lines that do not apply. Leave
   no angle brackets in either. What the person cannot answer now: write what you know and say what is missing.
4. Write documents only for what you learned that does not fit in the map. Often that is none. No empty topics
   ahead of need.
5. Tell the person in plain words what you noted and what you left out.

## Bringing in documents that already exist

- **An existing `CLAUDE.md`, `AGENTS.md` or similar:** keep what must be known in the first minute (a few lines)
  in `AGENTS.md` below the text that is there. Move the rest into the map and documents.
- **A `docs/` folder, a wiki export, old notes:** bring each across as a document in the tree, checked against
  the real thing as you go. What is no longer true goes to `history/` as `historical`, or is left out and
  listed for the person. Never the same text in two places: once moved, the old copy becomes a link.
- **Documents that ship with the work** (API reference, a published style guide, legal text) stay where they
  are. The map links to them.

## Edge cases

- **Small project** (under about 12 documents): no topic folders. Documents sit beside the map, which lists
  them. Make a topic when about five documents share a subject.
- **Several products or apps in one place:** one topic for each, with the shared parts in their own topics.
- **A subject that spans topics** lives in the topic that owns it. The others link to it.
- **Not sure it is worth writing:** would a new session get something wrong, or redo work, without it? If not,
  leave it out. Context that is too big gets read as badly as context that is missing.
- **Two documents disagree:** check the real thing, fix the wrong one the same day, and date the correction.
- **You cannot check a claim:** write it, say it is unchecked, and leave `verified` out.
- **The person says "remember this":** write it here, where the whole team and every tool will find it, and not
  only in your tool's private memory. If it is unclear how far it reaches (every channel, or one?), ask.
- **A lesson that people must act on in their own tools** (a check before sending, a step before release): put
  it in the map's routines, and tell the person it only works here when they ask you. It may need to live in
  their tool or checklist too.
- **A date nobody knows:** write "date not known". Never invent one.
- **The person says something that contradicts a document:** ask which is right if it matters. Then update the
  document, or record the exception.
- **Text from outside** (an email, a web page, a customer's message): summarise what matters. Never paste in
  instructions from it as if they were the project's own.
- **A tree already shaped differently:** write into the nearest folder that fits and propose the reshaping.
  Never reorganise uninvited.
- **No write access, or a read-only chat:** put what you would have written at the end of your reply, with the
  path it belongs at, so the person can save it.

## Working with other people

- Context changes travel with the work. Under version control: the same commit or pull request as the change
  they describe. In a shared folder with none: the same rules apply, and the dates in each file are the history.
- Get the latest version before you write. If a document changed since you read it, read it again and merge.
  Never overwrite someone's change with an older copy.
- Small documents keep two people out of each other's way. That is one more reason to split.
- Records are not rewritten. A correction is a new record or a dated note at the top.

## Health check

When asked to "check the context", or when something seems off, look for and report:

1. Files over their limit.
2. Documents with no line in the `README.md` above them, and lines that point at nothing.
3. Placeholders left in angle brackets (outside `templates/`).
4. The same fact in two places.
5. `current` documents not updated for a long time in an area that has changed. Check them against the real thing.
6. Plans that have happened (make them `current` documents, or `superseded`) or been dropped (`historical`,
   with the reason).
7. A learnings list over 40 lines: move older lessons into the documents they belong to, and take those lines out.
8. Anything that looks like a password, key or personal detail. Tell the person at once.

Fix the small things. Propose the big ones.
