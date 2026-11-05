# Every Part Every Day

A browser game for practising **EPE** ("every part every … days") and **SMED** in value stream mapping. It covers how often each stage can make every variant, which stage limits the plant, and how quicker changeovers get you to every part every day.

**Play it:** https://celiksuakd.github.io/every-part-every-day/

## The idea

Every stage has the same day: 2 shifts × (8 h − 30 min break) = **900 min**. Production and breakdowns use part of it, and only the time left over is available for set-ups.

```
EPE (days) = n × C/O ÷ time left for set-ups
time left  = T × share × A − D × units per product × C/T
```

The plant is only as flexible as its least flexible stage. In the game, every stage is drawn as a "day bar" so you can see what fits and what does not.

## Missions

### Mission 1: every variant, every day (Exercise 1, question 2)

Family A: 68 low-volume variants, 450 pcs/day, three dedicated stages.

| Stage | C/T (s) | C/O (min) | A |
|---|---|---|---|
| Machining | 95 | 10 | 95% |
| Heat treatment | 80 | 0 | 95% |
| Assembly | 105 | 0 | 100% |

The general manager wants every stage to make every variant every day.

1. Spot the stage that cannot.
2. Measure its time left for set-ups and its EPE.
3. Run a SMED workshop with a 14 k€ budget:
   - move work outside the machine stop
   - shorten what has to stay inside
   - decide whether TPM is worth it
4. Run a week to see the before/after effect on batches and cycle stock.

### Mission 2: what EPE can the plant promise? (Exercise 2, question 2)

Family B: 6 high-volume variants, 1,800 pcs/day.

| Stage | C/T (s) | C/O (min) | A | Share for family B | Units per product |
|---|---|---|---|---|---|
| Press | 4 per foil | 120 | 80% | 60% | 1 |
| Cutter | 10 per pipe | 15 | 100% | 70% | 2 |
| Welding | 10 | 0 | 100% | 100% | 1 |
| Drilling | 12 | 100 | 95% | 100% | 1 |
| Finishing | 23 | 0 | 100% | 100% | 1 |

1. Work out each stage's EPE. Hints are available, and common slips (forgetting the share, the availability or the second pipe) get tailored feedback.
2. Pick the company EPE and the stage that sets it.
3. Explain why the stage with a short set-up is the least flexible.

### What-if lab

A sandbox for both families. You can move C/O, availability, share and the target EPE, and every day bar and the company EPE update live.

## The course solution

**Exercise 1, Q2.** Machining has 900 × 0.95 − 450 × 95 ÷ 60 = 142.5 min/day left for set-ups. Making all 68 variants needs 68 × 10 = 680 min, so EPE = 680 ÷ 142.5 = **4.77 ≈ 5 days**. Heat treatment and Assembly have no set-ups.

EPE = 1 day needs 68 set-ups/day, so C/O ≤ 142.5 ÷ 68 = **2.10 min** (−79%). The answer is **SMED on Machining**. TPM alone (A = 100%) only lifts the limit to 2.76 min.

**Exercise 2, Q2.**

| Stage | Time left for set-ups (min/day) | n × C/O (min) | EPE (days) |
|---|---|---|---|
| Press | 432 − 120 = 312 | 720 | 2.31 |
| Cutter | 630 − 600 = 30 | 90 | **3.00** |
| Drilling | 855 − 360 = 495 | 600 | 1.21 |
| Welding, Finishing | – | 0 | 1 |

**Company EPE = 3 days, set by the cutter.** The cutter makes two pipes per product on 70% of its day, so it is 95% busy, and a 15-minute set-up still does not fit often.

## Modelling assumptions

- Available time is 900 min/day. Breakdowns take (1 − A) of the time a stage works for the family, and a shared machine works `share × 900` min for this family.
- A stage with no set-up time has EPE = 1 day.
- In Mission 1, only the 10-minute set-up and the 2.10-minute target come from the exercise. The split of the changeover into six elements, their times, the improvement costs and the 14 k€ budget are invented for the game.
- Batch per variant = D ÷ n × EPE. Average cycle stock = D × EPE ÷ 2.
- Best scores are stored only in your own browser (localStorage).

## Run locally

It is a single static file. Open `index.html` in any browser.

Built as a study aid for an Operations Management course (lean management, value stream mapping).
