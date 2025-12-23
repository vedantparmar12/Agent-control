# Context Engineering Template for OpenAI Codex

A comprehensive template for getting started with Context Engineering—the discipline of engineering context for AI coding agents (specifically OpenAI Codex) so they have the information necessary to get the job done end-to-end.

> **Context Engineering is 10x better than prompt engineering and 100x better than vibe coding.**

## 🚀 Quick Start

```bash
# 1. Clone this template
git clone https://github.com/vedantparmar12/Agent-control.git
cd Context-Engineering-Intro

# 2. Initialize Codex Session
# This reads AGENTS.md as the project's "Constitution"
codex

# 3. Inside the Codex TUI:
# Initialize project rules (if not already done)
/init

# 4. Create your initial feature request
# Edit INITIAL.md with your feature requirements

# 5. Generate a PRP (Product Requirements Prompt)
# Prompt Codex to generate a plan based on your request:
"Using INITIAL.md as input, and referencing the examples in examples/, research and generate a comprehensive Product Requirements Prompt (PRP) in PRPs/new-feature.md. Follow the structure in PRPs/templates/prp_base.md."

# 6. Execute the PRP
# Prompt Codex to build the feature:
"Execute the plan in PRPs/new-feature.md. Follow all validation gates and do not stop until all tests pass."
```

## 📚 Table of Contents

- [What is Context Engineering?](#what-is-context-engineering)
- [Template Structure](#template-structure)
- [Codex Integration](#codex-integration)
- [Writing Effective INITIAL.md Files](#writing-effective-initialmd-files)
- [The PRP Workflow](#the-prp-workflow)
- [Using Examples Effectively](#using-examples-effectively)
- [Best Practices](#best-practices)

## What is Context Engineering?

Context Engineering represents a paradigm shift from traditional prompt engineering:

- **Prompt Engineering**: Tweaking the "ask" (e.g., "Write this code carefully").
- **Context Engineering**: Curating the "knowledge" (e.g., providing a folder of 5 perfect examples, a rulebook, and a database schema before asking).

## Template Structure

```
context-engineering-intro/
├── AGENTS.md                  # The "Brain" of the project (formerly CLAUDE.md)
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md       # Base template for PRPs
│   └── EXAMPLE_multi_agent_prp.md
├── examples/                  # Golden samples for the AI to mimic
├── INITIAL.md                 # Template for feature requests
└── README.md                  # This file
```

## Codex Integration

This template is optimized for **OpenAI Codex (CLI v0.58.0+)**.

### `AGENTS.md` (The Rulebook)
Codex and other agents (like GitHub Copilot) use `AGENTS.md` as a standard context file. It tells the agent:
- **Build Commands**: How to run tests (`pytest`, `npm test`)
- **Style guide**: Formatting rules, preferred libraries.
- **Architectural Constraints**: "Max 500 lines per file", "Always use Pydantic".

### Essential Codex Slash Commands
Inside the TUI, use these to manage your session:
*   `/init`: Reads `AGENTS.md` to ground the session.
*   `/status`: Checks token usage and context.
*   `/diff`: Shows pending changes.
*   `/review`: Asks Codex to self-review its work.

## The PRP Workflow

**Product Requirements Prompts (PRPs)** are detailed blueprints generated *by* the AI, *for* the AI.

### Step 1: Research (Generate PRP)
Instead of a custom command, you simply ask Codex to do the research.
*Prompt:*
> "Read INITIAL.md. Search the web for documentation on [Libraries]. Look at `examples/` for patterns. Then write a detailed implementation plan in `PRPs/my-feature.md`."

### Step 2: Execution (Execute PRP)
Once the PRP is written, it becomes the instruction set.
*Prompt:*
> "Read `PRPs/my-feature.md`. Implement step 1. Run the validation command. If it passes, move to step 2."

## Using Examples Effectively

The `examples/` folder is **critical**.
*   **Do not rely on Codex's training data alone.** It might be outdated (e.g., using `pydantic` v1 instead of v2).
*   **Provide "Gold Standard" files.** If you want your CLI to look a certain way, put a `cli_example.py` in `examples/`. Codex will mimic the style, error handling, and argument parsing exactly.

## Best Practices

1.  **Trust `AGENTS.md`**: Update it often. If Codex keeps making the same mistake (e.g., "forgot to use async"), add a rule to `AGENTS.md`.
2.  **Validate often**: Use the `/review` command before committing large chunks of code.
3.  **Use Context Compaction**: Codex v0.58+ supports massive context windows, but it's still best to `/new` between unrelated tasks to keep the attention mechanism sharp.
