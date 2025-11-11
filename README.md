# Hog: Dice Game Simulator
[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)]() [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)]()

A Python implementation of the **Hog** dice game: simulator, strategies, commentary functions, and small Monte‑Carlo utilities.

> **Academic Integrity / Note**
> 
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
./dice.py         # Functions for rolling dice
./hog_gui.py      # A graphical user interface (GUI)
./ucb.py          # Utility functions for CS 61A
./gui_files/      # A directory of various things used by the web GUI
```
---

## ▶️ Quick Start

```
python3 hog_gui.py
```


---

