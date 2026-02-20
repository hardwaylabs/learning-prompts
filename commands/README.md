# Claude Code commands

This directory contains [custom slash commands][docs] for Claude Code.
Each `.md` file becomes a `/command` you can invoke inside a Claude Code session.

[docs]: https://docs.anthropic.com/en/docs/claude-code/skills

## Available commands

| Command | Description |
| ------- | ----------- |
| `/explore` | Guided exploration of an existing codebase or system |

## Installation

Copy command files to one of two locations depending on scope:

**Global** (available in every project):

```bash
cp commands/*.md ~/.claude/commands/
```

**Per-project** (available only in that repository):

```bash
cp commands/*.md /path/to/your/project/.claude/commands/
```

Create the target directory first if it doesn't exist:

```bash
mkdir -p ~/.claude/commands        # for global
mkdir -p .claude/commands          # for per-project (from repo root)
```

After copying, the commands are available immediately in new Claude Code sessions.
No restart is needed for already-running sessions - just start a new one.

## Usage

In a Claude Code session, type `/` followed by the command name:

```text
/explore the authentication system
/explore how data flows from API to database
/explore                           # Claude will ask what to focus on
```

Everything after the command name is passed as `$ARGUMENTS` to the prompt template.

## Commands vs skills

Claude Code has two mechanisms for custom slash commands:
**commands** and **skills**.
They create the same end result (a `/slash-command` you can invoke)
but differ in structure and capabilities.

### Commands (simpler)

A single markdown file in `.claude/commands/`:

```text
.claude/commands/
└── explore.md          # creates /explore
```

- One file per command
- Supports `$ARGUMENTS` for user input
- Good for self-contained prompt templates
- What this repository provides

### Skills (more powerful)

A directory with a `SKILL.md` entry point in `.claude/skills/`:

```text
.claude/skills/
└── explore/
    ├── SKILL.md        # creates /explore (required)
    ├── template.md     # supporting file (optional)
    └── examples/       # additional resources (optional)
```

Skills add capabilities that commands don't have:

- **Supporting files** - templates, examples, and scripts alongside the prompt
- **Invocation control** - restrict whether the user, Claude, or both can trigger it
- **Dynamic context** - inject shell command output into the prompt
  with `` !`command` `` syntax
- **Subagent execution** - run in an isolated context with `context: fork`
- **Frontmatter configuration** - control model, allowed tools,
  and other behavior

### Which to use

| Situation | Use |
| --------- | --- |
| Simple prompt template | Command |
| Needs supporting files (templates, examples) | Skill |
| Want Claude to auto-invoke when relevant | Skill (with invocation settings) |
| Need to inject live data (git diff, API output) | Skill (with `` !`command` ``) |
| Sharing with others (like this repo) | Command (simpler to copy) |
| Complex multi-step workflow | Skill |

Commands are a subset of skills.
If you start with a command and need more power later,
you can convert it to a skill by moving the file
into a `SKILL.md` inside a named directory under `.claude/skills/`.

## Creating your own

1. Create a `.md` file in this directory (or directly in `~/.claude/commands/`)
1. Write a prompt template using `$ARGUMENTS` where user input should go
1. The filename (without `.md`) becomes the command name
1. Test it by typing `/your-command-name` in a Claude Code session

See the [Claude Code documentation][docs] for the full reference.
