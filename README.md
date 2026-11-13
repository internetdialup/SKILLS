# SKILLS

Reusable agent skills organized by category.

| Category | Focus |
| --- | --- |
| [DESIGN](DESIGN/) | Design workflows |
| [GAMEDEV](GAMEDEV/) | Game development |
| [APPDEV](APPDEV/) | Application development |
| [CONTEXT](CONTEXT/) | Language, memory, and contextual understanding |
| [AI](AI/) | AI workflows |

## Available skills

### Lexicon / Idiom Context

[Skill](CONTEXT/lexicon-idiom-context/SKILL.md) · [Fictional examples](CONTEXT/lexicon-idiom-context/examples/README.md)

A growing private dictionary that helps agents understand your slang, idioms, nicknames, and conversational syntax. Global wording travels across projects; project-specific meanings stay tethered to their context. Retrieval temperatures prioritize useful knowledge, and redirects preserve references when objects move.

The complete `CONTEXT/lexicon-idiom-context/` folder is the installable skill. Use your agent host's skill installation mechanism, then invoke `$lexicon-idiom-context`.

This skill provides instructions, not a shared-memory service. Cross-agent continuity requires authorized access to the same private binder. The repository contains reusable instructions and fictional examples only; personal dictionaries belong in private storage.

## Repository conventions

Add each skill under its category as `<skill-name>/SKILL.md`, with only the supporting resources it needs. Keep names lowercase and hyphenated within the uppercase category folders. Follow [AGENTS.md](AGENTS.md) for contribution and privacy rules.
