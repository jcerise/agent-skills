# Jeremy's Agent Skills

A collection of custom skills for [Claude Code](https://claude.ai/code). Each skill defines a specialized behavior — a persona, workflow, or tool-augmented capability — that Claude activates when triggered by a matching request.

## Skills

| Skill | Description |
|---|---|
| [rubber-duck](rubber-duck/SKILL.md) | Interactive debugging partner that asks one question at a time to help you think through a problem, without reading your code or handing you the answer |
| [plan-architect](plan-architect/SKILL.md) | Creates detailed step-by-step implementation plans, saved to `./plans/`, with explicit file paths, function signatures, and acceptance criteria |
| [plan-executor](plan-executor/SKILL.md) | Executes plans from `./plans/` one step at a time, respecting review gates and tracking progress in the plan frontmatter |
| [learning-path-creator](learning-path-creator/SKILL.md) | Produces a research-grounded self-study curriculum for any topic, with concrete resources, phase goals, and synthesis activities |

## Installing a skill

Skills are `SKILL.md` files that Claude Code discovers in your project.

### Local Installation

1. **Copy the skill file** into your project (or anywhere Claude Code can find it):

   ```
   your-project/
   └── .claude/
       └── skills/
           └── rubber-duck/
               └── SKILL.md
   ```

   The location is flexible — Claude Code discovers `SKILL.md` files recursively. A `.claude/skills/` subdirectory is a common convention.

2. **Reference the skill** in your project's `CLAUDE.md` if you want to make it explicit, or just start a conversation — Claude Code will pick it up automatically from the file.

3. **Trigger the skill** by using a phrase that matches its description. For example:
   - `rubber-duck` — say "let me rubber duck this" or "help me think through a bug"
   - `plan-architect` — say "plan out this feature" or "architect the new auth flow"
   - `plan-executor` — say "execute the current plan" or "what's next?"
   - `learning-path-creator` — say "create a curriculum for Rust" or "help me learn distributed systems"

### Global Installation

To make a skill available across all your projects, place it in the Claude Code global skills directory:

```
~/.claude/skills/
└── rubber-duck/
    └── SKILL.md
```

### Writing your own skill

A `SKILL.md` file has a YAML frontmatter block and a freeform instruction body:

```markdown
---
name: my-skill
description: One sentence describing when to activate this skill. Include trigger phrases.
---

# My Skill

Instructions for Claude's behavior when this skill is active...
```

The `description` field is what Claude uses to decide whether to invoke the skill. Make it specific and include the phrases a user would naturally say.
