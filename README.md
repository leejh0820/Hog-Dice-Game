# Hog: Dice Game Simulator
[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)]() [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)]()

A Python implementation of the **Hog** dice game: simulator, strategies, commentary functions, and small Monte‑Carlo utilities.

> **Academic Integrity / Note**
> This project was completed in Fall 2021 at **UC Berkeley** for CS 61A: The Structure and Interpretation of Computer Programs. It is published for portfolio/educational purposes only—please do not reuse in active coursework.

---

## 🐷 Overview

* Two players race to a **goal score** (default **100**). Each turn, a player chooses **0–10** dice to roll.
* Special rules:
  * **Sow Sad**: If any die shows **1**, that turn’s score is **exactly 1**.
  * **Picky Piggy**: Rolling **0** dice yields the *n*‑th digit of `1/7 = 0.(142857)` where *n* is the opponent’s score; if *n* is 0, score **7**.
  * **Hog Pile**: After adding the turn score, if totals are **equal**, the current player’s total is **doubled**.

---

## 📁 Repository Layout & Naming

```
./hog.py          # main implementation
./dice.py         # dice utilities (fair/test)
./hog_gui.py      # GUI runner
./ucb.py          # helpers used by ok/tests
./gui_files/      # GUI static assets

```
---

## ▶️ Quick Start

```
python3 hog_gui.py
```


---

# Hog: Dice Game Simulator (CS61A‑style)

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)]() [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)]()

A Python implementation of the **Hog** dice game: simulator, strategies, commentary functions, and small Monte‑Carlo utilities.

> **Academic Integrity / Note**
> This project was originally completed ~4 years ago for learning purposes. It is published for portfolio/education only—please **do not** reuse in active coursework.

---

## 🐷 Overview

* Two players race to a **goal score** (default **100**). Each turn, a player chooses **0–10** dice to roll.
* Special rules:

  * **Sow Sad**: If any die shows **1**, that turn’s score is **exactly 1**.
  * **Picky Piggy**: Rolling **0** dice yields the *n*‑th digit of `1/7 = 0.(142857)` where *n* is the opponent’s score; if *n* is 0, score **7**.
  * **Hog Pile**: After adding the turn score, if totals are **equal**, the current player’s total is **doubled**.

---

## 📁 Repository Layout & Naming

> Repo name: **`hog-dice-game`** (kebab‑case is conventional for GitHub).
> Python files & packages: **snake_case** (underscores), import‑friendly.

```
# required (keep names for compatibility)
./hog.py          # main implementation
./dice.py         # dice utilities (fair/test)
./hog_gui.py      # GUI runner
./ucb.py          # helpers used by ok/tests
./ok              # autograder entry (binary/script)
./tests/          # ok tests (do NOT edit)
./gui_files/      # GUI static assets

# optional (you can add or rename these as you like)
./docs/           # screenshots, writeups
./assets/         # images/gifs used by README/GUI
./experiments/    # Monte‑Carlo sweeps, notebooks
./scripts/        # helper scripts (e.g., run_gui.sh)
```

**Why not rename `hog.py`, `tests/`, `ok`, `hog_gui.py`?**
They are referenced by the OK tests / GUI; renaming may break them. Add new folders instead of renaming required files.

---

## ▶️ Quick Start

```bash
# (optional) create and activate a virtual environment
python3 -m venv .venv && source .venv/bin/activate

# run problem‑specific tests
python3 ok -q 01
# overall progress
python3 ok --score

# run GUI (after play() is implemented)
python3 hog_gui.py
```

**Handy flags**

* `python3 ok -q <num> -i` → run tests for a problem, then interactive mode
* `python3 ok --submit` → back up/submit
* `python3 ok --local` → local only

---

## 🧠 Implementation Highlights

* `roll_dice(num_rolls, dice)` — call `dice()` exactly `num_rolls` times; any `1` → return **1**.
* `picky_piggy(opponent_score)` — 6‑cycle digit of `1/7` (or 7 if `opponent_score == 0`).
* `take_turn(num_rolls, opponent_score, dice, goal)` — 0‑roll (Picky Piggy) vs normal rolls.
* `hog_pile(player_score, opponent_score)` — equal totals after adding → return bonus equal to `player_score`.
* `play(strategy0, strategy1, dice, goal, say)` — single loop; **call commentary at the end of each turn**.
* Commentary: `say_scores`, `announce_lead_changes`, `both`, `announce_highest`.
* Experiments: `make_averaged`, `max_scoring_num_rolls`.
* Strategies: `picky_piggy_strategy`, `hog_pile_strategy`, `final_strategy`.

---

## 🧪 Examples

```python
from hog import *
from dice import make_test_dice

# Average of a deterministic dice stream
dice = make_test_dice(3, 1, 5, 6)
averaged_dice = make_averaged(dice, 1000)
print(averaged_dice())  # -> 3.75

# Best number of rolls for a constant die
print(max_scoring_num_rolls(make_test_dice(3)))  # -> 10
```

---

## 🎮 GUI

```bash
python3 hog_gui.py
```

Pick strategies and watch turn‑by‑turn updates.

---

## 🧭 Strategy Notes (brief)

* Roll **0** when it **wins immediately**, **triggers Hog Pile**, or **meets a cutoff** for Picky Piggy.
* Otherwise choose dice count based on lead/deficit and distance to goal (e.g., 3/4/5/6).

---

## 🔒 .gitignore

```gitignore
__pycache__/
*.pyc
.venv/
.env
.ok_history
.ok_storage
.pytest_cache/
.ipynb_checkpoints/
.DS_Store
.vscode/
.idea/
*.log
```

---

## 📜 License

Released under the **MIT License** (see `LICENSE`).

---

## 🙏 Acknowledgements

Based on the classic **CS 61A Hog** project specification.
