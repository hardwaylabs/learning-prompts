# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a collection of prompts for structured learning with AI assistants. There is no code to build, test, or lint - the repository contains only markdown files with prompt templates.

## Repository Structure

- `learning/` - Prompts for hands-on learning
  - `guided-project-construction.md` - Build projects incrementally with mentor-style guidance
  - `explore-existing-system.md` - Understand codebases or infrastructure through guided investigation
- `research/` - Prompts for evaluation
  - `technology-exploration.md` - Systematically assess new technologies
- `templates/` - Shared formats
  - `task-format.md` - Standard structure for learning tasks (Objective, Context, Steps, Hints, Success criteria, Capture)

## Design Philosophy

These prompts ask AI to **design learning experiences**, not provide answers. Key principles:
- Hints instead of solutions
- Discovery over explanation
- Scaffolded tasks with progressive complexity
- Space for productive struggle

Inspired by legitimate peripheral participation, "The Hard Way" style learning, and discovery-based pedagogy.

## When Modifying Prompts

- Keep bracketed placeholders (e.g., `[TECHNOLOGY]`, `[PROJECT TYPE]`) for users to fill in
- Maintain the mentor/guide voice rather than directive instruction
- Preserve the constraint against giving complete solutions
- Include example usage sections to clarify intended use
- Task format should target 30-60 minute chunks at medium difficulty
