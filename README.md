# moss

English | [Русский](README.ru.md)

A workspace for your notes and data that you share with your AI agent.

You keep a folder of ordinary files: Markdown, CSV, PDF, Excel, Word. moss shows that folder as pages, tables and charts, like Notion. Your agent (Claude Code, Codex or a local model) works in the same folder. You see every change it makes on the page, and you can undo any of them.

Cursor and T3 Code did this for code. moss does it for notes and personal data.

> This is an idea. There is no code yet.

## Why

Notion keeps your data on its servers and doesn't let you bring your own AI.

Obsidian keeps your files on your disk, but plain Markdown has little structure. Tables and charts need plugins.

You can already point Claude Code at an Obsidian vault. Then you read its changes as text diffs in a terminal, and nothing runs while you're away.

## How it works

Every page is a Markdown file. The header holds the page's properties, and the body holds its content:

```markdown
---
type: Post
status: Scheduled
publish: 2026-11-13 10:00
---
apps change. models change. your data stays.
```

A `type` gives a page its fields. You can add one at any time. Write plain notes first, and turn them into typed records once a pattern shows up.

To show other pages on a page, add a `view` block:

````markdown
```view
show: Post
where: status != Archived
layout: table
```
````

In moss this block is a live table you can edit with the mouse. In any other editor it is a short code block you can still read.

PDF, Excel and Word files open in their own editors inside moss and are saved in their own formats. You can put any file on a page and it shows a preview.

The workspace is a plain folder:

```
~/moss/
  AGENTS.md          rules for agents in this workspace
  Content/
    Posts.md
    posts/*.md       one post per file
  Health/
    food.csv
  .moss/             search index, history, types, agent settings
```

Delete `.moss/` and you lose the history and the index. Your notes stay.

## Rules

1. Your data is plain files on your disk.
2. You and the agent have the same tools. Anything the agent builds, you can build or change by hand.
3. Agent changes appear on the page itself, each with Accept and Undo.
4. Agents can run on a schedule. When they need a decision from you, they leave it in an Inbox.
5. Any agent works. moss runs the official Claude Code or Codex CLI, so you use your own subscription.

## Plan

1. Markdown pages, types and views.
2. An agent thread with visible changes and undo.
3. Scheduled agents and the Inbox.
4. PDF and CSV, then Excel and Word.
5. Sync, a phone app, self-hosting for teams.

Running moss locally will be free. We plan to charge for hosted AI, for sync, and for a server that runs your agents while your laptop is off.

moss is a working name.
