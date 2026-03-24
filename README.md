# rigor / dushno — Challenge Dial for Claude Code

A slash command skill that sets how critically Claude challenges your decisions, from zero pushback to maximum scrutiny.

> In Russian dev slang, a "душнила" (dushnila) is someone who suffocates you with questions and objections. This skill lets you dial that from 0 to 10.

## The Scale

| Level | EN Name | RU Name | Behavior |
|-------|---------|---------|----------|
| **0** | Bro | Бро | Zero questions. Just do it. |
| **1** | Chill | Чилл | Warns only if prod will literally break |
| **2** | Light | Лайт | Security and critical bugs only |
| **3** | Gentle | Мягкий | Soft suggestions, never insists |
| **4** | Constructive | Конструктивный | Mentions tradeoffs, accepts "no" |
| **5** | Balanced | Сбалансированный | Default mode — reasonable balance |
| **6** | Attentive | Внимательный | Clarifying questions, verifies assumptions |
| **7** | Critical | Критичный | Challenges architecture, demands justification |
| **8** | Thorough | Дотошный | Edge cases, scalability, error handling |
| **9** | Paranoid | Параноик | Challenges requirements, worst-case analysis |
| **10** | Dushnila | Душнила | Full devil's advocate. "Why build this at all?" |

## Usage

```
/rigor 0    — "fix this typo, don't ask questions"
/rigor 5    — normal feature work
/rigor 8    — new service, needs careful review
/rigor 10   — architecture decision, challenge everything

/dushno 0   — то же на русском
/dushno 10  — полный душнила-режим
```

## Install

Copy the skills to your Claude Code config:

```bash
# Global (all projects)
cp -r skills/rigor ~/.claude/skills/
cp -r skills/dushno ~/.claude/skills/    # optional, Russian alias

# Per-project
cp -r skills/rigor .claude/skills/
cp -r skills/dushno .claude/skills/
```

Or clone and symlink:

```bash
git clone https://github.com/spyrae/rigor-dushno.git ~/.claude/rigor-dushno
ln -s ~/.claude/rigor-dushno/skills/rigor ~/.claude/skills/rigor
ln -s ~/.claude/rigor-dushno/skills/dushno ~/.claude/skills/dushno
```

## When to Use What Level

- **0-2**: Trivial tasks, typos, quick fixes, README edits
- **3-4**: Standard features, well-understood changes
- **5**: Default — good for most work
- **6-7**: New features, API design, anything touching auth/payments
- **8-9**: Architecture decisions, new services, infrastructure
- **10**: "Should we even build this?" — product/strategy level scrutiny

## How It Works

The skill injects behavioral instructions into the conversation context. Claude adjusts its communication style — not its expertise. At level 0, it still writes correct code; it just doesn't question your approach. At level 10, it still writes the code — but only after a thorough interrogation.

## License

MIT
