# 8-Puzzle Solver using Greedy Best-First Search

## Overview
This implementation solves the 8-puzzle problem using the **Greedy Best-First Search** algorithm as described in Lab 04. The algorithm is an informed search method that uses heuristic functions to guide the search toward the goal state.

## Features

### Core Implementation
- **Greedy Best-First Search Algorithm**: Follows the exact steps from Lab 04
- **Multiple Heuristic Functions**:
  - Manhattan Distance (default)
  - Misplaced Tiles
- **State Management**: OPEN and CLOSED lists as specified
- **Solution Path Reconstruction**: Traces back from goal to initial state

### Key Components

#### 1. PuzzleState Class
Represents a state of the 8-puzzle with:
- 3x3 board configuration
- Parent state reference
- Move that led to this state
- Depth in search tree
- Heuristic value h(n)

#### 2. Heuristic Functions

**Manhattan Distance** (Recommended)
```python
def manhattan_distance(state, goal_state):
    """Sum of distances of each tile from its goal position"""
```
- More accurate heuristic
- Better performance in most cases
- Considers actual distance on the board

**Misplaced Tiles**
```python
def misplaced_tiles(state, goal_state):
    """Count of tiles not in their goal position"""
```
- Simpler heuristic
- Less informed than Manhattan distance
- May explore more nodes

#### 3. Algorithm Steps (from Lab 04)

**Step 1**: Place the starting node into the OPEN list
**Step 2**: If OPEN list is empty, return failure
**Step 3**: Remove node n with lowest h(n) from OPEN, add to CLOSED
**Step 4**: Expand node n and generate successors
**Step 5**: Check if any successor is the goal
**Step 6**: Add successors to OPEN list if not in OPEN or CLOSED
**Step 7**: Return to Step 2

## Usage

### Running the Program
```bash
python greedy_best_first_8puzzle.py
```

### Custom Puzzle
You can modify the `main()` function to solve your own puzzle:

```python
# Define initial state (0 represents blank tile)
initial_board = [
    [1, 2, 3],
    [4, 0, 5],
    [7, 8, 6]
]

# Define goal state
goal_board = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 0]
]

initial_state = PuzzleState(initial_board)
goal_state = PuzzleState(goal_board)

# Solve with Manhattan distance
solution, nodes_expanded, max_depth = greedy_best_first_search(
    initial_state, goal_state, manhattan_distance
)
```

### Board Representation
- Numbers 1-8 represent tiles
- 0 represents the blank space (displayed as *)
- Goal state: tiles in order with blank at bottom-right

```
1 2 3
4 5 6
7 8 *
```

## Algorithm Explanation

### Greedy Strategy
Greedy Best-First Search expands nodes with the **lowest heuristic value** h(n):
- h(n) = estimated distance from current state to goal
- Lower h(n) means closer to goal (presumably)
- Uses a priority queue to always expand most promising node

### Why "Greedy"?
- Makes locally optimal choice at each step
- Doesn't consider path cost g(n)
- Only looks at heuristic h(n)
- May not find optimal solution (but finds solution quickly)

### Comparison with A*
- Greedy: f(n) = h(n)
- A*: f(n) = g(n) + h(n)
- Greedy is faster but less optimal
- A* guarantees optimal solution (with admissible heuristic)

## Example Output

```
Starting Greedy Best-First Search...
Initial State:
1 2 3
4 * 5
7 8 6

Initial heuristic value: 2

Expanding node 1 (depth=0, h=2):
1 2 3
4 * 5
7 8 6

Expanding node 2 (depth=1, h=1):
1 2 3
4 5 *
7 8 6

Goal state found!

SOLUTION PATH
Step 0: Initial State
1 2 3
4 * 5
7 8 6

Step 1: Move Right
1 2 3
4 5 *
7 8 6

Step 2: Move Down
1 2 3
4 5 6
7 8 *

Total moves: 2
```

## Statistics Tracked
- **Nodes Expanded**: Total states explored
- **Maximum Depth**: Deepest level reached in search tree
- **Solution Depth**: Number of moves in solution path

## Important Notes

### Admissibility
From Lab 04: h(n) ≤ h*(n)
- h(n) = heuristic estimate
- h*(n) = actual cost to goal
- Both heuristics implemented are admissible

### Completeness
- Greedy Best-First Search is **not complete** in infinite spaces
- May get stuck in loops without cycle detection
- This implementation uses CLOSED list to avoid revisiting states

### Optimality
- Greedy Best-First Search does **not guarantee** optimal solution
- It finds *a* solution quickly, not necessarily the *best* solution
- For optimal solutions, use A* search instead

## Advantages
✓ Fast for problems where heuristic is accurate
✓ Uses less memory than breadth-first search
✓ Good for finding quick solutions
✓ Works well when goal is "nearby"

## Limitations
✗ Not guaranteed to find optimal solution
✗ Can be misled by inaccurate heuristics
✗ May explore unnecessary paths
✗ Performance depends heavily on heuristic quality

## Extensions

You can extend this implementation to:
1. Add more heuristic functions
2. Implement iterative deepening
3. Add visualization of the search process
4. Handle larger puzzles (15-puzzle, 24-puzzle)
5. Compare with A* search algorithm

## References
- Lab 04: Informed Searches in Artificial Intelligence
- Russell & Norvig: Artificial Intelligence - A Modern Approach
- Greedy Best-First Search Algorithm specifications
