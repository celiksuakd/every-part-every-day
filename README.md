# Value Stream Game: Family B

A browser game for **Exercise 2** of a lean value stream mapping exercise set:

- **Question 1:** draw the current state map of family B.
- **Question 2:** find the EPE ("every part every … days") of every stage and of the plant.

It also includes a bonus mission on Exercise 1, question 2, and a what-if lab.

**Play it:** https://celiksuakd.github.io/every-part-every-day/

## The case (family B)

Six high-volume variants (B1…B6), 1,800 pcs/day, sold every day and delivered twice a day. The plant runs two 8-hour shifts with a 30-minute break each. The press and the cutter work in parallel and are shared with other families. Welding joins one foil and two identical pipes, then drilling, finishing and shipping. The supplier delivers weekly, so 13 days of foils and 13 days of pipes are in stock.

| Stage | C/T (s) | C/O (min) | A | Share for family B | Units per product | Stock after |
|---|---|---|---|---|---|---|
| Press | 4 per foil | 120 | 80% | 60% | 1 | 20,000 |
| Cutter | 10 per pipe | 15 | 100% | 70% | 2 | 21,600 |
| Welding | 10 | 0 | 100% | 100% | 1 | 4,000 |
| Drilling | 12 | 100 | 95% | 100% | 1 | 5,000 |
| Finishing | 23 | 0 | 100% | 100% | 1 | 30,000 |

## Question 1: finish the intern's current state map

The map is already drawn with the standard VSM icons. You complete it in five steps:

1. **Takt time:** type it into the customer data box.
2. **Inventory days:** convert every stock triangle into days of demand.
3. **Timeline:** compute the production lead time and choose the value-added time.
4. **Check the map:** the intern made six mistakes in the icons, information flows and data boxes. Click any label, arrow or data-box line and set what it should show. Changing a correct item costs points.
5. **Your map:** see what you fixed, compare with the corrected map, and read why each item looks the way it does.

## Question 2: what EPE can the plant promise?

1. Work out the EPE of the press, cutter and drilling. Hints are available, and common slips get tailored feedback: forgetting the share, the availability or the second pipe.
2. Pick the company EPE and the stage that sets it.
3. Explain why the stage with the short set-up is the least flexible.

## The course solution

**Question 1**

- Takt time = 2 × (480 − 30) min × 60 ÷ 1,800 = **30 s**.
- Inventory days:

  | Stock | Calculation | Days |
  |---|---|---|
  | After the press | 20,000 ÷ 1,800 | 11.11 |
  | After the cutter | 21,600 ÷ (2 × 1,800) | 6.00 |
  | After welding | 4,000 ÷ 1,800 | 2.22 |
  | After drilling | 5,000 ÷ 1,800 | 2.78 |
  | Finished goods | 30,000 ÷ 1,800 | 16.67 |

- Lead time (longest branch, through the press) = 13 + 11.11 + 2.22 + 2.78 + 16.67 = **45.78 days**.
- Value-added time = max(4 s ; 2 × 10 s) + 10 + 12 + 23 = **65 s**.
- It is a push system:
  - push arrows between all stages
  - weekly production plan to every process
  - daily dispatch plan to Shipping
  - weekly supplier deliveries, deliveries to customers twice a day
  - customers send daily orders for next-day delivery and a 30/60/90-day forecast
  - PP sends the supplier a 30/60-day forecast and a weekly order confirmation

**Question 2**

`EPE = n × C/O ÷ (T × share × A − D × units × C/T)`

| Stage | Time left for set-ups (min/day) | n × C/O (min) | EPE (days) |
|---|---|---|---|
| Press | 432 − 120 = 312 | 720 | 2.31 |
| Cutter | 630 − 600 = 30 | 90 | **3.00** |
| Drilling | 855 − 360 = 495 | 600 | 1.21 |
| Welding, Finishing | – | 0 | 1 |

**Company EPE = 3 days, set by the cutter.** The cutter makes two pipes per product on 70% of its day, so it is 95% busy and has almost no time left for set-ups.

## Bonus and lab

- **Bonus, Exercise 1 Q2:** family A has 68 variants. You find why machining blocks "every part every day" (EPE 4.77 days), then reach C/O ≤ 2.10 min in a SMED workshop on a budget.
- **What-if lab:** move C/O, availability, share and the target EPE, and every day bar and the company EPE update live.

## Modelling assumptions

- Available time is 900 min/day. Breakdowns take (1 − A) of the time a stage works for the family. A shared machine works `share × 900` min for this family.
- Parallel branches: the lead time follows the longest branch. The value-added time counts press and cutter once, with the longer time per product (cutter: 2 × 10 s).
- The intern's mistakes in question 1 are invented for the game. So are the SMED breakdown, costs and budget in the bonus mission.
- Best scores are stored only in your own browser (localStorage).

## Run locally

It is a single static file. Open `index.html` in any browser.

Built as a study aid for an Operations Management course (lean management, value stream mapping).
