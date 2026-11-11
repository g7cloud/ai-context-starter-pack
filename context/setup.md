---
summary: "How to set the context up the first time, and how to bring in instructions and documents a project already has."
status: current
updated: 2026-11-11
---
# Setting the context up

Used once, when the map still has `<placeholders>`, and again whenever existing material is brought in.
Up: [the map](README.md).

## First setup

1. Look at what is already here: the names of the files and folders, any README, recent history. Read what
   tells you what the project is. Leave the detail (source code, raw research material) for the tasks that
   need it. Do not ask for what you can read.
2. Ask the person at most five short questions for what you cannot: what this is and who it is for, its state
   and owner, the rules that must never be broken, where the real thing lives, and what an AI keeps getting
   wrong here (for writing work: how it should sound, with an example they like). Skip any they have already
   answered.
3. Fill in the map, `now.md` and the learnings list. Delete the sections and lines that do not apply
   (passwords, routines, topics, words). Where a list has nothing in it yet, write "None yet". Leave no angle
   brackets in any of the three. What nobody could answer goes in `now.md` under open questions.
4. Write documents only for what you learned that does not fit in the map. Often that is none. No empty topics
   ahead of need.
5. Tell the person in plain words what you noted and what is still missing.

## Bringing in what already exists

- **An existing `CLAUDE.md`, `AGENTS.md` or similar:** keep what must be known in the first minute (a few lines)
  in `AGENTS.md` below the text that is there. Move the rest into the map and documents.
- **A `docs/` folder, a wiki export, old notes:** bring each across as a document in the tree, checked against
  the real thing as you go. What is no longer true goes to `history/` as `historical`, or is left out and
  listed for the person. Never the same text in two places: once moved, the old copy becomes a link.
- **Documents that ship with the work** (API reference, a published style guide, legal text) stay where they
  are. The map links to them.
- **A project with no version control:** for a code project, suggest it once. Never set it up uninvited.
