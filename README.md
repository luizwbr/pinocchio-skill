# 🪵 Pinocchio Skill

A reusable prompt skill that turns every AI response into a self-evaluated answer with a **Hallucination Detector** block — so you always know how confident the model really is.

---

## What it does

After every response, Copilot appends a **Pinocchio Score** block that shows:

- **Confidence percentage** (how sure the model is overall)
- **Number of uncertain claims** (things that might be wrong, outdated, or inferred)
- **A collapsible list** of those claims with a brief explanation

Example output with 0 uncertain claims:

```
---
🪵 **Pinocchio Score:** 97% confidence | ✅ 0 uncertain claims
```

Example output with uncertain claims:

```
---
🪵 **Pinocchio Score:** 72% confidence | 🔶 2 uncertain claim(s)

<details>
<summary>See uncertain claims</summary>

- ❓ The `--flag` option exists in v3.x — couldn't verify without running the command
- ❓ Default port is 3000 — may differ depending on framework version

</details>
```

### Score emoji guide

| Range | Emoji |
|-------|-------|
| 95–100% | ✅ |
| 80–94% | ⚠️ |
| 60–79% | 🔶 |
| 0–59% | 🔴 |

---

## Supported AIs

| AI | Status | Skill file |
|----|--------|------------|
| GitHub Copilot | ✅ Supported | `.github/skills/pinocchio/SKILL.md` |
| Claude | ✅ Supported | `.claude/skills/pinocchio/SKILL.md` |
| Any agent | ✅ Supported | `.agents/skills/pinocchio/SKILL.md` |

---

## Usage

### Setting up the skill directory

Skills are stored in a `skills` directory inside a supported location. Choose the scope that fits your needs:

**Project skills** (specific to a single repository):

```
.github/skills/pinocchio/SKILL.md
.claude/skills/pinocchio/SKILL.md
.agents/skills/pinocchio/SKILL.md
```

**Personal skills** (shared across all your projects):

```
~/.copilot/skills/pinocchio/SKILL.md
~/.claude/skills/pinocchio/SKILL.md
~/.agents/skills/pinocchio/SKILL.md
```

> **Important:** Skill files must be named `SKILL.md`. Skill subdirectory names should be lowercase and use hyphens for spaces.

### Installing the Pinocchio skill

1. Create a `skills` directory in one of the supported locations above.
2. Create the `pinocchio` subdirectory inside it:
   ```
   mkdir -p .github/skills/pinocchio
   ```
3. Copy [`SKILL.md`](.github/skills/pinocchio/SKILL.md) from this repository into that directory.
4. The skill is now available in your AI assistant. Invoke it by referencing it in your chat:
   ```
   #pinocchio <your question here>
   ```

### Using with Claude

Copy `SKILL.md` into `.claude/skills/pinocchio/SKILL.md` (project) or `~/.claude/skills/pinocchio/SKILL.md` (personal). The skill will be picked up automatically by any Claude-based agent that reads from those paths, or paste the contents as a system prompt in any Claude client.

---

## Self-evaluation rules

Before appending the block, the model honestly evaluates:

- Did I state anything I'm not 100% sure about?
- Could anything have changed since my training cutoff?
- Did I infer instead of know?
- Is there any code I couldn't actually run and verify?

A low real score is better than a high fake one.

---

## License

MIT

