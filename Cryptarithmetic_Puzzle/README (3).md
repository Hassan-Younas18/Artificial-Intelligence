# Cryptarithmetic Puzzle Solver

A Python implementation of AI search algorithms to solve cryptarithmetic puzzles using BFS and DFS approaches.

## 📋 Table of Contents
- [About](#about)
- [Problem Description](#problem-description)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Algorithms](#algorithms)
- [Results](#results)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Contributing](#contributing)
- [License](#license)

## 🎯 About

This project implements two different search algorithms (BFS and DFS) to solve cryptarithmetic puzzles - a classic AI constraint satisfaction problem where letters represent unique digits and must satisfy an arithmetic equation.

**Academic Project**: Part of Artificial Intelligence course assignment focusing on search algorithms and problem-solving techniques.

## 🧩 Problem Description

Cryptarithmetic puzzles are mathematical problems where:
- Numbers are represented by letters or symbols
- Each letter represents a unique digit (0-9)
- The objective is to find the correct digit-letter mapping
- Leading digits cannot be zero
- The mapping must satisfy the given arithmetic equation

### Example
```
  SEND
+ MORE
-------
 MONEY
```
Solution: S=9, E=5, N=6, D=7, M=1, O=0, R=8, Y=2

## ✨ Features

- **Multiple Search Algorithms**: Implements both BFS and DFS approaches
- **Generic Solution**: Works with any cryptarithmetic puzzle format
- **Performance Metrics**: Calculates and displays running time for each algorithm
- **Clean Output**: Displays solutions in an organized, readable format
- **Validation**: Ensures all constraints are satisfied

## 🚀 Installation

1. Clone the repository:
```bash
git clone https://github.com/Hassan-Younas18/cryptarithmetic-solver.git
cd cryptarithmetic-solver
```

2. Ensure you have Python installed (Python 3.6 or higher):
```bash
python --version
```

3. Install required dependencies:
```bash
pip install jupyter notebook
```

## 💻 Usage

### Running in Jupyter Notebook

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open `Cryptarithmetic Puzzle.ipynb`

3. Run the cells to see the algorithms in action

### Modifying the Puzzle

You can test different puzzles by changing the input:

```python
# For BFS
puzzle = ["SEND", "MORE", "MONEY"]
solution, running_time = solve_cryptarithmetic(puzzle)

# For DFS
puzzle = ["LOGIC", "LOGIC", "PROLOG"]
solution, running_time = solve_cryptarithmetic(puzzle)
```

### Other Popular Puzzles to Try

```python
# Easy
puzzle = ["TWO", "TWO", "FOUR"]

# Medium
puzzle = ["CROSS", "ROADS", "DANGER"]

# Hard
puzzle = ["SATURN", "URANUS", "PLANETS"]
```

## 🔍 Algorithms

### 1. Breadth-First Search (BFS)

**Approach**: Explores all possible assignments level by level

**Characteristics**:
- Explores the search space systematically
- Guarantees finding a solution if one exists
- Higher memory usage due to queue storage

**Time Complexity**: O(n! × validation_time) where n is the number of unique characters

**Space Complexity**: O(n! × state_size)

**Performance**: ~3.58 seconds for SEND + MORE = MONEY

### 2. Depth-First Search (DFS)

**Approach**: Uses backtracking to explore assignments depth-first

**Characteristics**:
- Explores one complete path before backtracking
- Memory efficient (only stores current path)
- Prunes invalid assignments early
- Faster in practice due to early termination

**Time Complexity**: O(10^n) in worst case, much better with pruning

**Space Complexity**: O(n) where n is recursion depth

**Performance**: ~0.23 seconds for LOGIC + LOGIC = PROLOG

## 📊 Results

### Test Case 1: SEND + MORE = MONEY (BFS)
```
Solution: D=7, E=5, M=1, N=6, O=0, R=8, S=9, Y=2
Running Time: 3.58 seconds
```

### Test Case 2: LOGIC + LOGIC = PROLOG (DFS)
```
Solution: C=8, G=6, I=4, L=2, O=9, P=0, R=5
Running Time: 0.23 seconds
```

### Performance Comparison

| Algorithm | Time (seconds) | Memory Usage | Efficiency |
|-----------|---------------|--------------|------------|
| BFS       | 3.58          | High         | ⭐⭐       |
| DFS       | 0.23          | Low          | ⭐⭐⭐⭐⭐ |

**Winner**: DFS is approximately **15x faster** and more memory efficient for this problem type.

## 📁 Project Structure

```
cryptarithmetic-solver/
│
├── Cryptarithmetic Puzzle.ipynb          # Main Jupyter notebook with implementations
├── README.md               # Project documentation
└── Project_Description.pdf              # Detailed Project Description
```

## 📦 Requirements

- Python 3.6+
- Jupyter Notebook
- Standard libraries:
  - `collections` (deque)
  - `itertools`
  - `time`

## 🔬 Key Observations

1. **DFS Superiority**: For cryptarithmetic puzzles, DFS with backtracking significantly outperforms BFS due to early pruning of invalid branches.

2. **Memory Efficiency**: DFS uses O(n) space compared to BFS's O(n!) space requirement.

3. **Practical Performance**: While both algorithms guarantee finding a solution, DFS finds it much faster in practice.

4. **Optimization Potential**: Both implementations can be further optimized with:
   - Constraint propagation
   - Leading zero elimination
   - Carry-forward validation

## 🤝 Contributing

This is an academic project, but suggestions and improvements are welcome:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

## 📝 License

This project is part of an academic assignment. Feel free to use it for learning purposes with proper attribution.

## 👤 Author

**Hassan Younas**
- Roll No: 21I-1788
- Course: Artificial Intelligence
- Institution: FAST National University

## 🙏 Acknowledgments

- Course instructor for problem formulation and guidance
- AI search algorithm concepts from course materials
- Python community for excellent documentation

---

**Note**: This implementation is designed for educational purposes to demonstrate AI search algorithms and problem-solving techniques.

## 📧 Contact

For questions or feedback, please open an issue in the repository or contact p.hassan.ph@gmail.com

---

⭐ **Star this repository** if you found it helpful!
