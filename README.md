# Training Incentive Designer

A WorkBuddy skill that designs complete, ready-to-deliver **employee training incentive schemes** based on the "dual-track parallel" methodology.

## What's Inside

| File | Purpose |
| --- | --- |
| `SKILL.md` | Methodology + 9-step workflow that WorkBuddy follows when triggered |
| `references/camel-scheme-full.md` | A complete, real-world reference scheme (骆驼员工培训激励方案 V2.0) |
| `references/design-principles.md` | Behavior-economics rationale behind every design choice |
| `assets/scheme-template.md` | Parameterized template with `{{...}}` placeholders, ready to fill in |

## The Methodology in 30 Seconds

Two complementary tracks replace the failure modes of single-track rewards:

- **Track A — Streak-Increment**: the weekly champion gets a voucher that grows by a fixed increment each consecutive win (e.g., 19 → 39 → 59 → 79 → 99 元), capped at a maximum. Drives sustained engagement via **loss aversion**.
- **Track B — Guaranteed-Base**: runners-up (#2, #3) get a fixed small voucher. Prevents discouragement and keeps the mid-tier in the game.

Together they maintain a competitive atmosphere across the entire top tier without runaway costs.

## When WorkBuddy Uses This Skill

WorkBuddy loads this skill when the user asks to:

- "Design a training incentive plan"
- "Create an employee reward scheme for learning"
- "Build a streak-based points reward system"
- "员工培训激励方案设计"
- "学习平台奖励机制"

## How to Use Locally

```bash
# Clone
git clone https://github.com/haoranx968/training-incentive-designer.git

# Copy into your WorkBuddy skills directory
cp -r training-incentive-designer ~/.workbuddy/skills/

# Trigger in WorkBuddy
# "帮我设计一个员工培训激励方案"
```

## License

MIT — see [LICENSE](LICENSE).