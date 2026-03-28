# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** M.Spandana  
**Student ID    :** 2310040117  
**Date Submitted:** 28-03-2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
[ The count_clashes() function measures the number of conflicts in the timetable, such as exams scheduled at the same time for students or resource overlaps. A lower value indicates fewer conflicts. A value of 0 means a perfect timetable with no clashes. ]
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
[The generate_neighbor() function creates a new timetable by making a small random change to the current timetable, such as swapping time slots or reassigning an exam. The new timetable is slightly different but similar to the current one. This helps explore nearby solutions in the search space. ]
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
[ This line decides whether to accept the new solution or not. If the new solution has fewer clashes (delta < 0), it is always accepted. If it is worse, it may still be accepted with a probability based on temperature, which helps avoid getting stuck in local minima. ]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379 |
| Clashes at iteration 1 |12 |
| Final best clashes |3 |
| Did SA reach 0 clashes? (Yes / No) |No |

**Copy the printed timetable output here:**
```
[  Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
  Total clashes : 3 ]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
[The plot shows a rapid decrease in clashes during the initial iterations, indicating quick improvement. The biggest drop happens early as the algorithm quickly removes major conflicts. After that, the curve gradually flattens, showing slower improvements as it approaches an optimal solution. ]
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|----------------|----------------------|--------------------|
| 0.80        |      8         |     31               |       No             |
| 0.95        |       3        |     135              |       No           |
| 0.995       |        3       |     1379             |       No            |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
[With a cooling rate of 0.80, the temperature drops very quickly, so the algorithm converges fast but does not explore enough, resulting in a higher number of clashes. With 0.95, the cooling is slower, allowing more exploration and leading to fewer clashes. With 0.995, the cooling is very slow, giving the algorithm the most time to explore, but in this case it still did not reach 0 clashes, though it performed better than 0.80. Overall, slower cooling improves solution quality but increases the number of iterations. ]
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
[The cooling rate of 0.95 and 0.995 gave the best results with 3 clashes. Among them, 0.995 is slightly better because it allows more exploration due to slower cooling. This helps the algorithm search a larger solution space and avoid getting stuck too early. ]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3 |The algorithm reduces clashes quickly and stabilizes near an optimal solution. |
| 2 — Cooling rate | cooling_rate = ___ |3 |Slower cooling produces better solutions by allowing more exploration. |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[ From these experiments, I learned that Simulated Annealing is a powerful optimization technique that balances exploration and exploitation. The cooling rate plays a crucial role in determining the quality of the solution. Fast cooling leads to quick convergence but often results in suboptimal solutions, while slow cooling allows better exploration and improved outcomes. However, even with slow cooling, reaching a perfect solution is not guaranteed. Proper tuning of parameters is essential for achieving the best performance. ]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
