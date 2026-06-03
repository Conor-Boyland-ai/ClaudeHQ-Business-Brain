# Build Standards

Best practices for building agents and skills in this system. Every new agent
or skill must pass these checks. Loaded on demand, not every session.

## Agent files

**Format.** YAML frontmatter + markdown body. Frontmatter holds `name`,
`description`, `tools`. The body becomes the system prompt.

- `name`: kebab-case (lowercase letters, numbers, hyphens).
- `description`: specific and action-oriented. Says WHEN to invoke (trigger
  phrases) and WHAT the agent does. Third person. This is how Claude picks the
  right agent.
- `tools`: comma-separated. Only grant what the agent needs.

**Body rules.**
- One clear responsibility per agent. Not multi-purpose.
- Target ~500 words. Hard ceiling 1500.
- Slim agent file, rich context files. Detailed rules live in context/, not in
  the agent body.

**Required sections:** Identity, Read on every session, What you own, What you
do NOT own, Tools you can call, Self-improvement loop.

## Skill files

**Format.** SKILL.md = YAML frontmatter + markdown body.

- `name`: lowercase, hyphens, gerund form preferred (e.g. `writing-emails`).
- `description`: third person. What it does + when to use it.

**Body rules.**
- Overview, not encyclopedia. Target ~1500 words.
- One capability per skill. If it does two things, it's two skills.
- Procedure, not philosophy. A stranger should be able to follow it.
- Split into supporting files when it gets long.

## Anti-patterns (what breaks Claude)

- Bloated agent files with too many sections.
- Multi-purpose agents trying to be everything.
- Description fields that are labels, not triggers.
- Loose files at root with no folder structure.
- Memory sprawl.
- Detailed rules stuffed into the agent body instead of context files.

## Folder structure (keep it clean)

```
Claude HQ/
├── CLAUDE.md                 (constitution, <500 words)
├── context/                  (static knowledge)
├── agents/[agent-name]/      (agent file + feedback.md)
├── skills/                   (installed skills)
└── projects/                 (active work)
```

- Each agent gets its own folder. Memory lives next to its agent.
- Files under 1500 words.
- No loose files at root beyond CLAUDE.md. No empty folders.

## Process rules

1. Apply these standards before writing the first line.
2. Slim by default. Bloat is the enemy.
3. Capture rules in the right file the first time.
4. Notion is the long-term backup. Local is the daily driver.
