# Design Principles for Dual-Track Training Incentives

This document explains the design rationale behind the methodology used in `camel-scheme-full.md`. Read it when the user questions specific design choices, or when adapting the scheme to a different company context.

## 1. Why "Dual-Track" Instead of Single-Track

### The two failure modes of single-track

| Single-track design | Failure mode |
| --- | --- |
| Only the champion gets a reward | Mid-tier (#2, #3, #4) employees see the gap as insurmountable and give up by mid-season. Top-tier ranking becomes a fixed hierarchy of 2-3 people. |
| Everyone gets the same reward | No competitive drive. Employees stop differentiating effort because the outcome is the same regardless. |

### How dual-track solves both

- **Track A (streak-increment)** creates *aspirational scarcity*. The increment ladder makes the goal visible and the cost of losing tangible. Loss aversion ("I don't want to lose my 59-yuan streak") is empirically a stronger motivator than equivalent gain ("I'd like to get 99 yuan").
- **Track B (guaranteed-base)** creates *emotional safety*. A 10-yuan consolation for #2/#3 prevents the "effort was wasted" feeling when the difference between #1 and #2 is just 1 point.

Together they keep the top 3 employees all engaged: #1 chases the streak, #2/#3 chase the #1 spot knowing they still get something if they fall short.

## 2. Why a Streak Ladder, Not a Flat High Reward

### Behavior economics: loss aversion vs. equivalent gain

Kahneman & Tversky's prospect theory shows losses loom larger than gains. If a champion stands to **lose** a 59-yuan voucher by failing to win this week, that threat is psychologically heavier than the prospect of **gaining** 59 yuan by winning.

A streak ladder exploits this:

- Week 1: 19 yuan (baseline, no loss yet)
- Week 2: 39 yuan (now there's something to lose)
- Week 3: 59 yuan (more to lose → more engagement)
- ...
- Week 5+: 99 yuan (cap; the loss is now maximally painful)

The capped design prevents cost blow-out while preserving the maximum psychological effect at the top of the ladder.

### Why reset on any non-#1 finish

Some schemes reset only on extended absence. This is wrong. The reset must be on **any** non-#1 finish because:

- Otherwise, a runner-up who knows they can't overtake the leader has nothing to lose by skipping weeks. The streak becomes decoupled from effort.
- The "1-point difference" scenario is exactly when loss aversion should kick in hardest. If a near-miss doesn't reset the streak, the scheme teaches employees that near-misses are safe — undermining the very mechanism.

## 3. Why Three Weighted Dimensions (40/40/20)

The weights must balance **effort vs. outcome**:

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Learning | 40% | Inputs (hours studied). Necessary but prone to gaming without a daily cap. |
| Exam | 40% | Outcomes (knowledge tested). The most reliable signal of actual learning. |
| Activity | 20% | Engagement (notes, Q&A). Important for community building but lower direct value. |

Critical sub-rules:

- **Daily cap on learning hours** prevents time-farming (e.g., leaving a course playing in the background).
- **Best score of the week** for exams prevents penalty-seeking (re-taking bad scores).
- **Weekly cap on activity score** prevents comment-spamming.

Tiebreaker priority (`Exam > Learning > Activity`) ensures the scheme rewards *learning*, not *engagement gaming*.

## 4. Why a Cap and Circuit Breakers

Without caps, a single champion holding a 10-week streak would consume 990 yuan of voucher budget alone. At scale across regions, this is unbounded.

Three layers of protection:

1. **Per-employee cap** (e.g., 99 yuan): prevents runaway individual cost.
2. **Per-region monthly circuit breaker** (100% of budget): converts over-spend to 2x APP points. This protects the budget while still rewarding employees (points can be used for year-end evaluation bonuses).
3. **Annual hard cap**: when reached, scheme automatically converts to point-based. This is the last-resort control and signals that the budget envelope has been hit.

The **80% monthly warning threshold** is critical — it gives ops a chance to investigate and adjust before the hard breaker trips.

## 5. Why Cross-Departmental Red Lines Are Non-Negotiable

The Camel scheme was once rejected because it touched store scheduling (a store-ops red line). The four red lines codified in the current scheme exist because of this history:

1. **No scheduling interference**: store-ops will reject any scheme that influences shift assignment. Reward must be based purely on app data.
2. **No work-hour consumption**: HR/legal will reject any scheme that effectively extends the working day. Learning must happen on employees' own time.
3. **HQ pays**: store P&L owners will reject any scheme that charges stores for HQ-driven initiatives. Cost must come from HQ training budget.
4. **Stores benefit only**: stores must perceive a net positive (extra foot traffic + HQ subsidy per voucher redeemed) or they will quietly sabotage the scheme.

**Lesson**: When designing any cross-departmental scheme, identify the rejection-prone department *first*, then design the red lines to address their specific objections. Document their "interest point" explicitly so reviewers can see that the scheme was designed with their concerns in mind.

## 6. Why Dual-Channel Voucher Redemption

Employees have heterogeneous preferences:

- Some want a free item with no cash outlay → welfare mall (Channel A)
- Some want maximum perceived value and are willing to top up → store-wide discount (Channel B)

Channel A costs the company ~40-50% of face value (because the SKU cost is lower). Channel B costs the full face value but drives incremental sales.

**Critical**: do not force a single channel. Forcing Channel A frustrates employees who want choice; forcing Channel B loses the cost advantage. The dual-channel design lets the company serve both segments while maintaining margin flexibility.

The "no cash-back on difference" rule is important: if unused voucher value refunded as cash, employees will hoard small vouchers and never redeem, defeating engagement.

## 7. When to Adapt (and When Not To)

This methodology is suitable for:

- Companies with 100+ employees in a learning/knowledge-work domain
- Scenarios where learning behavior is voluntary (not mandated by compliance training)
- Reward budgets in the range of ¥50–100 per top-3 employee per week

It is NOT suitable for:

- Sales roles (use commission structures instead)
- Compliance training (use attendance penalties, not rewards)
- Very small teams (top-3 is meaningless if the whole team is 5 people)
- One-off training events (use a single prize-draw, not a sustained program)

## 8. Common Adaptation Questions

**Q: Can we use cash instead of vouchers?**
A: Yes, but cash has weaker "engagement-to-retail" linkage. Vouchers create a flywheel (engagement → voucher → store visit → upsell). Cash breaks the flywheel.

**Q: Can we skip Track B and only have Track A?**
A: Only if your top tier is large enough that missing #1 is genuinely close to a real loss. For teams where one person consistently wins, Track B is essential to keep others engaged.

**Q: Can the streak cap be removed?**
A: No. Removing the cap creates unbounded liability. If 99 yuan feels insufficient, raise it but keep the cap.

**Q: What if the disconnection rate is much lower than 80%?**
A: Re-cost the model. The 80% figure is an empirical average for Camel; other companies may differ. Always run a pilot before scaling.