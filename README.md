# Minesweeper AI Solver 💣🤖

An intelligent agent that plays the classic game of **Minesweeper** using **Propositional Logic**, **Set Theory**, and **Knowledge-Based Reasoning**. 

Developed as part of Harvard University's **CS50’s Introduction to Artificial Intelligence with Python (CS50AI)** course.

---

## 📌 Project Overview

Unlike traditional search engines or board games that evaluate every possible model (which becomes computationally intractable for Minesweeper due to $2^{N}$ possible states), this AI represents knowledge as **logical sentences** combining a set of undetermined cells with a count of neighboring mines:

$$\{A, B, C, D, E, F, G, H\} = 1$$

Using this knowledge representation, the AI makes deterministic logical inferences to identify guaranteed safe moves and mine positions without guessing whenever possible.

---

## ✨ Features & Logical Mechanics

- **Knowledge Base Representation:** Stores information efficiently using Python `set` data structures to represent logical sentences.
- **Automated Inference Engine:**
  - **Safe Cell Detection:** Infers that all cells in a sentence are safe when `count = 0`.
  - **Mine Detection:** Identifies cells as guaranteed mines when `len(cells) == count`.
  - **Subset Inference Rule:** Compares pairs of sentences ($S_1 \subset S_2$) to deduce new knowledge:
    $$(S_2 - S_1) = (Count_2 - Count_1)$$
- **Recursive Knowledge Updates:** Updates the internal knowledge base continuously whenever a cell is revealed or marked.
- **Fallback Strategy:** Executes a safe move (`make_safe_move`) with 0% risk if available; otherwise, calculates and picks a random move (`make_random_move`) among unrevealed non-mine cells.

---

## 📂 Project Structure

```text
.
├── minesweeper.py    # Main AI logic (Sentence & MinesweeperAI classes)
├── runner.py         # Pygame graphical user interface
├── requirements.txt  # Project dependencies
└── README.md         # Project documentation
