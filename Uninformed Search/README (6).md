# 8-Puzzle Solver using Breadth First Search

A Python implementation of the classic 8-puzzle problem solver using the Breadth First Search (BFS) uninformed search algorithm.

## 📋 Table of Contents
- [About the Project](#about-the-project)
- [The 8-Puzzle Problem](#the-8-puzzle-problem)
- [Algorithm Overview](#algorithm-overview)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Example Output](#example-output)
- [How It Works](#how-it-works)
- [Performance](#performance)
- [License](#license)

## 🎯 About the Project

This project implements a solution to the 8-puzzle problem using **Breadth First Search (BFS)**, an uninformed search algorithm. The implementation was created as part of LAB 03 - Uninformed Searches coursework, demonstrating how BFS can find optimal solutions to sliding puzzle problems.

## 🧩 The 8-Puzzle Problem

The 8-puzzle consists of a 3×3 grid containing eight numbered tiles (1-8) and one blank space. The objective is to rearrange the tiles from an initial configuration to a goal configuration by sliding tiles into the blank space.

**Example:**

```
Initial State:          Goal State:
+---+---+---+          +---+---+---+
| 2 | 8 | 3 |          | 1 | 2 | 3 |
+---+---+---+          +---+---+---+
| 1 | 6 | 4 |          | 8 |   | 4 |
+---+---+---+          +---+---+---+
| 7 |   | 5 |          | 7 | 6 | 5 |
+---+---+---+          +---+---+---+
```

## 🔍 Algorithm Overview

**Breadth First Search (BFS)** is an uninformed search algorithm that:
- Explores all nodes at the current depth before moving to nodes at the next depth level
- Uses a **queue** (FIFO) data structure to maintain the frontier
- Guarantees finding the **optimal solution** (shortest path)
- Is **complete** - will always find a solution if one exists

### Why BFS for 8-Puzzle?

- ✅ Finds the shortest solution path
- ✅ Complete algorithm (guaranteed to find solution)
- ✅ Simple and easy to understand
- ⚠️ Can be memory-intensive for deep solutions
- ⚠️ May explore many states before finding the goal

## ✨ Features

- **Optimal Solution Finding**: Always finds the shortest path to the goal
- **State Management**: Tracks visited states to avoid infinite loops
- **Move Validation**: Ensures only valid tile movements
- **Solution Path Reconstruction**: Shows step-by-step moves from start to goal
- **Performance Metrics**: Reports number of nodes explored
- **Clear Visualization**: Displays board states in a readable format

## 🚀 Getting Started

### Prerequisites

- Python 3.6 or higher
- No external dependencies required (uses only Python standard library)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/8-puzzle-bfs-solver.git
cd 8-puzzle-bfs-solver
```

2. Run the solver:
```bash
python eight_puzzle_bfs.py
```

## 💻 Usage

### Basic Usage

Simply run the script with the default puzzle configuration:

```bash
python eight_puzzle_bfs.py
```

### Custom Puzzle Configuration

Modify the `initial_state` and `goal_state` variables in the main section:

```python
# Define your own initial state
initial_state = [
    [2, 8, 3],
    [1, 6, 4],
    [7, 0, 5]  # 0 represents the blank space
]

# Define your own goal state
goal_state = [
    [1, 2, 3],
    [8, 0, 4],
    [7, 6, 5]
]
```

### Programmatic Usage

```python
from eight_puzzle_bfs import bfs_solve, print_solution

# Define puzzle states
initial = [[2, 8, 3], [1, 6, 4], [7, 0, 5]]
goal = [[1, 2, 3], [8, 0, 4], [7, 6, 5]]

# Solve the puzzle
solution = bfs_solve(initial, goal)

# Display the solution
print_solution(solution)
```

## 📊 Example Output

```
8-PUZZLE SOLVER USING BREADTH FIRST SEARCH
========================================

Initial State:
2 8 3
1 6 4
7   5

Goal State:
1 2 3
8   4
7 6 5

Searching for solution using BFS...
----------------------------------------
Solution found! Nodes explored: 20

========================================
Solution found in 5 moves!
========================================

Initial State:
2 8 3
1 6 4
7   5

Step 1: UP
2 8 3
1   4
7 6 5

Step 2: UP
2   3
1 8 4
7 6 5

Step 3: LEFT
  2 3
1 8 4
7 6 5

Step 4: DOWN
1 2 3
  8 4
7 6 5

Step 5: RIGHT -> GOAL STATE
1 2 3
8   4
7 6 5
```

## 🔧 How It Works

### Core Components

1. **PuzzleState Class**
   - Represents a board configuration
   - Tracks parent state for path reconstruction
   - Generates valid neighbor states
   - Checks for goal state

2. **BFS Algorithm**
   ```python
   def bfs_solve(initial_state, goal_state):
       - Initialize queue with start state
       - While queue is not empty:
           - Dequeue front node
           - Check if goal reached
           - Generate valid neighbors
           - Add unvisited neighbors to queue
       - Return solution or None
   ```

3. **State Space Management**
   - Uses set to track visited states
   - Converts board to tuple for hashing
   - Prevents revisiting states (cycle detection)

### Algorithm Flow

```
Start State → Queue
    ↓
Dequeue → Check Goal? → Yes → Solution Found!
    ↓ No
Generate Neighbors
    ↓
Filter Visited States
    ↓
Enqueue New States
    ↓
Repeat
```

## ⚡ Performance

### Complexity Analysis

- **Time Complexity**: O(b^d)
  - b = branching factor (~2-4 for 8-puzzle)
  - d = depth of solution

- **Space Complexity**: O(b^d)
  - Stores all nodes in memory

### Example Performance

| Puzzle Difficulty | Moves | Nodes Explored | Time |
|------------------|-------|----------------|------|
| Easy (5 moves)   | 5     | 20             | <0.1s |
| Medium (10 moves)| 10    | ~500           | ~0.5s |
| Hard (20 moves)  | 20    | ~10,000        | ~5s  |

### Limitations

- **Memory Usage**: BFS stores all explored states, which can be significant for deep solutions
- **Not Optimal for Deep Solutions**: For puzzles requiring many moves, informed search algorithms (A*, IDA*) perform better
- **Solvability**: Not all 8-puzzle configurations are solvable (the program will report if no solution exists)

## 🎓 Educational Value

This implementation demonstrates:
- Queue-based search algorithms
- State space representation
- Graph traversal techniques
- Path reconstruction
- Cycle detection in graphs
- Optimal pathfinding

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation

## 📧 Contact

Your Name - your.email@example.com

Project Link: [https://github.com/yourusername/8-puzzle-bfs-solver](https://github.com/yourusername/8-puzzle-bfs-solver)

## 🙏 Acknowledgments

- Lab assignment based on classic AI problem-solving techniques
- Inspired by Russell & Norvig's "Artificial Intelligence: A Modern Approach"
- BFS algorithm implementation follows standard AI textbook approaches

---

⭐ If you found this project helpful, please consider giving it a star!
