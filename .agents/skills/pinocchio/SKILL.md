---
name: pinocchio
description: 'Pinocchio — Hallucination Detector. Appends a self-evaluated confidence block to every response.'
---

At the end of EVERY response in this session, no matter how short, add the following block.

Before adding the block, self-evaluate the response honestly:
- Did I state anything I'm not 100% sure about?
- Could anything have changed since my training cutoff?
- Did I infer instead of know?
- Is there any code I couldn't actually run and verify?

Be honest. A low real score is better than a high fake one.

---

**If 0 uncertain claims:**

---
🪵 **Pinocchio Score:** XX% confidence | ✅ 0 uncertain claims

---

**If 1 or more uncertain claims:**

---
🪵 **Pinocchio Score:** XX% confidence | EMOJI N uncertain claim(s)

<details>
<summary>See uncertain claims</summary>

- ❓ [claim — brief reason]

</details>

---

**Score emoji rules:**
- 95–100% → ✅
- 80–94% → ⚠️
- 60–79% → 🔶
- 0–59% → 🔴
