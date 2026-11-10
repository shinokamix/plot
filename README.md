# moss

English | [Русский](README.ru.md)

**Your folder of files. Your agent. Every change it makes is visible and reversible.**

moss is an open source, local-first workspace for notes and personal data, built for AI agents. You keep a folder of plain files: Markdown, CSV, PDF, Word, Excel. moss shows it as a workspace with pages, tables and charts, similar to Notion. Agents you already use, such as Claude Code, Codex or a local model, work in the same folder with you.

The short version: Cursor and T3 Code did this for code. moss does it for your notes and data.

> Status: idea stage. Nothing works yet. This README describes what we plan to build.

## Why

- Notion is closed. You can't bring your own AI, and your data lives on someone else's server.
- Obsidian keeps your files, but a folder of Markdown has little structure. Tables, charts and typed records need plugins.
- Trackers for food, money or habits each lock data in their own app. You can't ask an AI to analyze all of it together.
- Obsidian plus Claude Code in a terminal already works, but you see agent changes as raw text diffs. Nothing runs in the background, and nothing asks for your permission in a clear way.

## What it is

### For a person

- **Home** shows what agents did overnight, what is waiting for you, and one input to write or ask anything.
- **Page** is an editor like Notion on top of a `.md` file. There is no separate edit mode and view mode. You can open an agent next to the page, and it sees the same page you do.
- **Thread** is a full conversation with an agent. It shows what the agent read, what it changed and when, with checkpoints you can restore.
- **Inbox** collects questions and permission requests from agents, such as "can I read Sleep?" or "add a Top posts view?".

### For an agent

An agent sees an ordinary folder plus a few conventions:

```
~/moss/
  AGENTS.md                 how this workspace is organized, rules, glossary
  Content/
    Posts.md                a page with a live view
    posts/
      P-43 apps change.md   one post, one file
  Health/
    Food.md
    food.csv                hundreds of small records in one table
    blood-test-nov.pdf
  .moss/
    index.db                search, fields, history (rebuildable)
    types/post.yaml         fields of the Post type
    skills/x-stats/         SKILL.md and a script
    agents/writer.md        role, access, schedule
```

Agents read and write files. For queries such as "all drafts" and for history they use the `moss` CLI or MCP server. Agents already know how to work like this in code repositories.

## How pages work

Everything is a page. A page is a Markdown file. Its frontmatter holds the properties, and its body holds the blocks.

```markdown
---
type: Post
status: Scheduled
publish: 2026-11-13 10:00
idea: "[[P-31 launch angle]]"
views: 0
---
apps change. models change. your data stays.
```

A type is a label with fields, not a folder. Every file with `type: Post` shows up in post views, wherever it lives. You can add a type later: write plain notes first, and when a pattern appears, you or an agent turn them into typed records.

A page can show data from other pages with a `view` block. This is the same approach Obsidian Bases, Dataview and Mermaid use:

````markdown
# Posts

```view
show: Post
where: status != Archived
layout: table
columns: [status, format, publish, views]
```
````

In moss this block is a live table you can edit with a mouse. In any other editor it is a readable code block.

A page holds three kinds of blocks:

1. Text: paragraphs, headings, lists, tasks, quotes, code.
2. Files: images, PDF, Excel, Word, audio. Each shows a preview and opens in its own editor inside moss.
3. Views: a table, board, calendar, chart or single number over other pages and CSV rows.

## Rules

1. Your data is plain files in a folder. If `.moss/` is deleted, you lose history and cache, not data.
2. A person and an agent use the same actions. An agent has no blocks that you can't add from the `/` menu, and you can edit by hand anything an agent made.
3. Agent changes show up on the page itself: new text is highlighted, a changed number shows its old value, and every change has Accept and Undo.
4. Agents work in the background on a schedule or on events. When they need you, they write to Inbox and don't block you.
5. External data, such as post stats from X, comes in through Sources: small scheduled jobs that write to files. Views only read.
6. Any agent works. moss runs the official CLI of Claude Code, Codex or a local model, so you use your own subscription.

## Files

| Format | In moss |
|---|---|
| `.md` | full page editor |
| `.csv` | table editor |
| `.pdf` | viewer with highlights. An agent can extract records with a link back to the page |
| images, audio, video | viewer, plus OCR and transcripts |
| `.xlsx` | spreadsheet editor. Agent edits are highlighted per cell |
| `.docx` | document editor. Agent edits arrive as Word tracked changes |

Every file is saved in its own format, so you can still open it in Excel, Word or Obsidian.

## Who it is for

The first users are people who already work with Claude Code or Codex every day and keep notes in Obsidian or Notion. Examples of what they can build by asking an agent:

- a content plan for X with post stats that refresh every morning;
- a food and weight log from photos and chat;
- a reading list, a job search tracker, spending from bank statements, flashcards from notes.

## Plans for money

- Local use is free and complete.
- Paid inference for people who don't have a subscription or don't want to spend their limits.
- Paid sync and hosting, so you don't have to set it up yourself.
- A paid always-on box where your agents and Sources run while your laptop sleeps.
- Self-hosting for teams and companies, including local models.

## Roadmap

1. Folder of Markdown files, page editor, types and `view` blocks over frontmatter.
2. Agent thread with visible changes, history and undo through Claude Code and Codex.
3. Sources and background agents, Inbox.
4. CSV and PDF, then Excel and Word.
5. Sync, mobile capture, team self-hosting.

## Name

moss is a working name.
