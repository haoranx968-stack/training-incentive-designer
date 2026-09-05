---
name: training-incentive-designer
description: This skill should be used when the user needs to design an employee training incentive scheme, build a learning-app-based reward mechanism, or gamify a corporate learning platform. It provides a proven "dual-track parallel" methodology (Track A: streak-increment for the champion + Track B: guaranteed-base for runners-up), including cost-control mechanisms, cross-departmental boundary rules, and a structured document template. Triggers on requests such as "design a training incentive plan", "create an employee reward scheme for learning", "build a streak-based points reward system", "员工培训激励方案设计", "学习平台奖励机制". The output is a complete, ready-to-deliver scheme document in Markdown.
agent_created: true
---

# Training Incentive Designer

## Overview

This skill helps the user design a complete, ready-to-deliver employee training incentive scheme based on the "dual-track parallel" methodology: **Track A (streak-increment)** drives long-term engagement through loss aversion, while **Track B (guaranteed-base)** prevents discouragement among runners-up. The methodology is grounded in behavior economics (loss aversion, diminishing marginal utility) and includes built-in cost control (caps, circuit breakers) plus strict cross-departmental boundary rules to avoid conflicts with store operations.

The output is a structured Markdown document with eight standard chapters, ready for stakeholder review.

## When to Use This Skill

Use this skill when the user asks to:

- Design an employee training incentive plan / scheme
- Build a reward system based on app learning data (e.g., a corporate learning platform like 骆驼学堂)
- Gamify a learning platform with streaks, rankings, or vouchers
- Convert an existing training program into a reward-driven engagement system
- Redesign an existing incentive scheme that is suffering from "gift fatigue" or "give-up after mid-season"

**Do NOT use this skill** for: sales commissions, OKR bonuses, one-time prize draws, or non-learning-related employee rewards.

## Methodology: Dual-Track Parallel

The core insight: a single reward track either creates excessive pressure (only the champion wins) or excessive complacency (everyone gets the same). Two complementary tracks solve both:

| Track | Mechanism | Behavior Driven | Cost Profile |
| --- | --- | --- | --- |
| **A: Streak-Increment** | Champion gets a voucher that grows by a fixed increment each consecutive week, capped | Loss aversion ("afraid to lose progress") drives sustained effort | Variable, capped; high for long streaks |
| **B: Guaranteed-Base** | Runners-up (#2, #3) get a fixed small voucher | Prevents discouragement, keeps mid-tier employees engaged | Fixed and predictable |

**Why dual-track works**: Track A creates aspirational scarcity; Track B provides emotional safety. Together they maintain a competitive atmosphere across the entire top tier.

## Workflow

Follow these steps in order. Reference `references/design-principles.md` for detailed rationale and `assets/scheme-template.md` for the output skeleton.

### Step 1: Gather Inputs

Ask the user for the following before drafting (use `AskUserQuestion` if needed):

1. **Platform**: Which app/system will track learning data? (e.g., 骆驼学堂, custom LMS, generic learning platform)
2. **Employee scope**: Full-time only, or include part-time? Region-based ranking or national?
3. **Budget envelope**: Per-employee weekly cap? Annual budget ceiling?
4. **Reward type**: Vouchers (with what brand/products?), cash, points, or merchandise?
5. **Past failure modes**: Has a previous scheme been rejected? By which department? Why?
6. **Settlement cycle**: Weekly, bi-weekly, monthly?

### Step 2: Define Statistics & Ranking Rules

Establish three weighted dimensions (typical weights, adjust to context):

- **Learning score (40%)**: required course hours + extra elective hours, with a daily cap to prevent "time farming"
- **Exam score (40%)**: best quiz/exam result of the week
- **Activity score (20%)**: high-quality notes, helpful Q&A, with a weekly cap

Define ranking tiebreaker priority: `Exam > Learning > Activity`. Define the ranking scope (region is typical).

### Step 3: Design Track A (Streak-Increment)

Construct the denomination ladder. Recommended pattern:

| Consecutive Wins | Voucher | Increment |
| --- | --- | --- |
| Week 1 | base | — |
| Week 2 | base + X | +X |
| Week 3 | base + 2X | +X |
| ... | ... | +X |
| Week N and above | cap | +X (capped) |

Define **disconnection rules** explicitly:
- Any non-#1 finish resets streak to 0 (even if #2 or #3)
- Any week with zero activity resets streak
- Resuming a streak after disconnection starts from base, not from prior high

Document with a worked example (e.g., 3 wins → 4th week slips to #2 → 5th week wins again from base).

### Step 4: Design Track B (Guaranteed-Base)

Fixed small denomination (typically much smaller than Track A base) for #2 and #3. Clarify:
- Does Track B interact with Track A streak? (Recommended: no — streak belongs only to A, B is pure consolation)
- Can a #1 also receive Track B? (Recommended: no — A and B are mutually exclusive per person per week)

### Step 5: Design Settlement & Distribution

Typical weekly schedule:

| Time | Action | Trigger |
| --- | --- | --- |
| Mon 00:30 | Settle scores, generate ranking | Cron |
| Mon 00:35 | Compute streak status for each employee | Cron |
| Mon 00:40 | Issue Track A vouchers to champions | Cron |
| Mon 00:45 | Issue Track B vouchers to #2, #3 | Cron |
| Mon 08:00 | Push weekly report & winner list to all employees | Cron |

### Step 6: Define Voucher Usage Rules

Choose **dual-channel redemption**:
- **Channel A**: Welfare mall — fixed SKU pool (10–15 items), voucher covers cost, employee pays nothing extra
- **Channel B**: Store-wide unconditional discount — employee can apply on any product, pays the difference if total exceeds voucher

Include risk controls:
- Daily voucher redemption cap per employee (e.g., 1/day)
- Identity verification at redemption (prevent transfer)
- 3-day expiry reminder push
- Abnormal concentration monitoring (alert on bulk redemption at a single store)

### Step 7: Cost Control & Circuit Breakers

Set hard caps and define circuit breakers:

| Level | Trigger | Response |
| --- | --- | --- |
| Monthly warning | Region spend reaches 80% of monthly budget | Email alert to ops owner |
| Monthly breaker | Region spend reaches 100% | Over-spend converted to 2x APP points; cash vouchers resume next month |
| Annual cap | Total spend reaches annual budget | Stop vouchers; switch all to APP points |

Provide cost projection tables (theoretical max vs. expected average, factoring in ~80% disconnection rate).

### Step 8: Cross-Departmental Boundary Rules (CRITICAL)

If the user's company has multiple departments that might conflict with the scheme (e.g., store operations), define the four red lines:

1. **No scheduling interference**: rewards based on app data only, never on shifts/overtime
2. **No work-hour consumption**: learning happens on employees' own time
3. **HQ pays**: full cost from HQ training budget, never charged to stores
4. **Stores benefit only**: stores only scan to redeem; HQ subsidizes by redemption volume

For each stakeholder, document the "interest point" — what they gain — to make buy-in easier.

### Step 9: Generate the Output Document

Use `assets/scheme-template.md` as the skeleton. Fill in all eight chapters:

1. 总则 (General Principles) — purpose, principles, stakeholder responsibilities
2. 统计与排名规则 (Statistics & Ranking Rules)
3. 奖励机制设计 (Reward Mechanism Design) — Tracks A and B, settlement flow
4. 购物券使用规则 (Voucher Usage Rules) — properties, dual-channel, risk control
5. 成本控制 (Cost Control) — caps, projections, circuit breakers
6. 跨部门协作边界 (Cross-Departmental Boundaries) — red lines, stakeholder interests
7. 名词解释 (Glossary)
8. 附则 (Supplementary Provisions) — effective date, interpretation right, feedback channel

Deliver as a Markdown file, optionally saved to a workspace folder, and present via `present_files`.

## Output Format

The final document should follow these conventions:

- **Document metadata table** at the top (编号、版本、拟制人、评审部门、保密等级、发布日期)
- **Revision history table** with version, date, content, author
- **Chapter headings** as `#`, sections as `##`, sub-sections as `###`
- **Tables** for all structured rules (weights, caps, schedules, red lines)
- **Bold** for design intent, core principles, and exception handling
- **Worked examples** in blockquotes for non-obvious calculations (e.g., streak reset scenarios)

## Resources

### references/

- `camel-scheme-full.md` — The complete original 骆驼员工培训激励方案 (V2.0) as a reference template. Read when the user wants to see a fully worked example or compare their draft against the canonical version.
- `design-principles.md` — Detailed design rationale extracted from the Camel scheme: behavior economics foundation, why dual-track beats single-track, why caps and reset rules matter, why cross-departmental red lines are non-negotiable. Read when the user questions specific design choices.

### assets/

- `scheme-template.md` — A blank, parameterized template with all eight chapters pre-structured. Copy this, then fill in placeholders (`{{...}}`) with the user's specific values. This is the primary deliverable scaffold.

## Iteration Notes

- If the user wants to change a denomination ladder, always also update the disconnection rule section — they are coupled.
- If the user is redesigning a previously rejected scheme, dig into **why** it was rejected (which department, what red line was crossed) before drafting.
- Cost projection tables must distinguish **theoretical max** (assumes everyone maxes out) from **expected average** (factors in ~80% disconnection rate). Both are needed for budget approval.