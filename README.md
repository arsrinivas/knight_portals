# ♟️ Knights and Portals

A simple web-based tool to find the shortest path from a Start (S) to an End (E) point on a grid, navigating around walls (1), empty spaces (0), and using teleport portals (P) to jump between specific cells in one step.

---

## Description

This project lets you enter a grid layout where:

- `S` = Start position
- `E` = End position
- `0` = Empty cell (walkable, no teleport)
- `1` = Wall (not walkable)
- `P` = Portal cell (special teleport points)

The program computes the shortest number of steps to reach from `S` to `E`. Movement is allowed in 4 directions (up, down, left, right), one step at a time.

You can **teleport once** from any portal `P` cell to any other portal `P` cell, which counts as **1 step**.

---

## How to Use

1. Input your grid into the textarea. Each row is a line of characters representing the grid cells.
2. Click **Find Shortest Path**.
3. The output below will show:
   - ✅ Shortest Path: *X* steps, if path exists
   - ❌ No Path Found, if no path is possible

---

## Example Grids and Expected Results

| Grid Input                   | Description                      | Expected Output              |
|-----------------------------|--------------------------------|-----------------------------|
| ```                         | Start at top-left, end bottom-right, no portals | ✅ Shortest Path: 6 steps    |
| S000                        |                                |                             |
| 0000                        |                                |                             |
| 0000                        |                                |                             |
| 000E                        |                                |                             |
| ```                         |                                |                             |
| ```                         | Includes two portals P; teleport may shorten path | ✅ Shortest Path: 5 steps    |
| S000                        |                                |                             |
| 0P00                        |                                |                             |
| 00P0                        |                                |                             |
| 000E                        |                                |                             |
| ```                         |                                |                             |
| ```                         | No valid path due to walls     | ❌ No Path Found             |
| S100                        |                                |                             |
| 1100                        |                                |                             |
| 0011                        |                                |                             |
| 00E1                        |                                |                             |

---

## Notes

- Teleportation can be used only once per path and only between two different portal cells `P`.
- Walls `1` block movement.
- The shortest path accounts for walking and optionally one teleport jump.
- If no path exists, the program returns no path found.

---

## How It Works (Brief)

- Uses Breadth-First Search (BFS) from `S` to compute distances.
- Uses BFS from `E` to compute distances back.
- Checks all portal pairs to calculate if teleporting between them reduces the overall path.
- Returns the minimum walking + teleport steps.

---

## Run Locally

Simply open the `index.html` file in any modern web browser. Edit the grid and click the button to test paths.

---

