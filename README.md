# Learning prompts

A collection of prompts for structured learning with AI assistants.

## Philosophy

Traditional tutorials teach you to build something from scratch, step by step. But real-world learning rarely works that way. Engineers join projects mid-stream, inherit complex systems, and need to understand existing code before they can contribute.

This repository contains prompts that flip the script: instead of asking an AI to explain concepts or generate solutions, these prompts ask the AI to **design learning experiences** - scaffolded projects with incremental tasks, hints instead of answers, and space for productive struggle.

The approach is inspired by:

- **Legitimate peripheral participation** - learning by engaging with authentic, complete systems
- **Kelsey Hightower's "Kubernetes The Hard Way"** - understanding through deliberate manual effort
- **Discovery-based learning** - exploring existing structures exercises different mental muscles than following construction steps

## When to use these prompts

- You want to learn a new framework, language, or tool
- No good tutorial exists yet (common with emerging technologies)
- You learn better by doing than by reading
- You want to build genuine understanding, not just surface familiarity

## Repository structure

```text
prompts/
├── learning/
│   ├── guided-project-construction.md  # Build a project incrementally with tasks
│   ├── explore-existing-system.md      # Understand a codebase or system
│   └── socratic-dialogue.md            # Discover insights through guided questioning
├── research/
│   └── technology-exploration.md       # Evaluate a new technology systematically
└── templates/
    └── task-format.md                  # Standard format for learning tasks
```

## Quick start

1. Choose a prompt that matches your learning goal
2. Copy it into your AI assistant conversation (Claude, Claude Code, etc.)
3. Fill in the bracketed placeholders with your specific context
4. Optionally, append the task format from `templates/task-format.md` for more structured output
5. Follow the generated task sequence, asking for hints when stuck
6. Document what you learn as you go

For detailed instructions on combining prompts with the task format template, see `templates/task-format.md`.

## Example: learning a new framework

Using `guided-project-construction.md`:

```markdown
# Learning mode: guided project construction

I want to learn [Google Genkit] by building a [conversational agent with tool use] incrementally.
Do NOT build the complete solution for me.

## Your role
Act as a technical mentor designing a learning path...
```

The AI will create minimal scaffolding, one example function, and a sequence of tasks with hints - not complete solutions.

## Contributing

These prompts improve through use. If you find a prompt that needs refinement:

1. Note what went wrong or could be clearer
2. Submit a PR with your improvement
3. Include a brief explanation of the problem you encountered

## Background

This project is part of [Hard Way Labs](https://github.com/hardwaylabs), which develops hands-on technical training materials that expose the mechanics typically hidden by frameworks and abstractions.

Created by [Pavel Anni](https://pavelanni.dev), a technical training architect with 35+ years of experience teaching distributed systems, Kubernetes, and AI-assisted development.

## License

MIT - use these prompts however you like, adapt them to your needs, share them with others.
