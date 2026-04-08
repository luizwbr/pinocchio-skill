# 🪵 Pinocchio Skill

A GitHub Copilot reusable prompt that turns every AI response into a self-evaluated answer with a **Hallucination Detector** block — so you always know how confident the model really is.

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

## Usage

This skill is a [GitHub Copilot reusable prompt](https://docs.github.com/en/copilot/customizing-copilot/reusing-prompts-and-instructions-in-copilot-chat) stored in `.github/prompts/pinocchio.prompt.md`.

### Option 1 — Use it in your own repo

1. Copy `.github/prompts/pinocchio.prompt.md` into your repository.
2. In Copilot Chat, type:
   ```
   #pinocchio <your question here>
   ```
3. Every response will include the Pinocchio Score block.

### Option 2 — Reference it as a workspace instruction

Add the content of `pinocchio.prompt.md` to your `.github/copilot-instructions.md` file to apply it automatically to all Copilot interactions in that repository.

### Option 3 — Use it in a single session

Paste the contents of `pinocchio.prompt.md` directly into Copilot Chat to activate the skill for the current session only.

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

