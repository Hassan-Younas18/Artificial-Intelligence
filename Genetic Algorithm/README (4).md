# Artificial Intelligence Assignment: Genetic Algorithm & Multi-Variant Linear Regression

## 📋 Project Overview

This repository contains implementations of two fundamental AI concepts as part of an academic assignment:

1. **Genetic Algorithm for Intrusion Detection** - Feature selection for network intrusion classification
2. **Multi-Variant Linear Regression** - Predicting daily productivity from personal routine data

---

## 📂 Repository Structure

```
├── GeneticAlgorithm.ipynb           # GA implementation for intrusion detection
├── Multi-Variant_Linear_Regression.ipynb  # MLR implementation from scratch
├── Project_Description.pdf          # Original assignment requirements
├── README.md                        # Project documentation
└── data/                           # Dataset files (not included)
    ├── UNSW_NB15_training-set.parquet
    ├── UNSW_NB15_testing-set.parquet
    └── routine_dataset.csv
```

---

## 🔬 Question 1: Genetic Algorithm for Intrusion Detection

### Overview
Implementation of a Genetic Algorithm to perform feature selection on the UNSW-NB15 network intrusion dataset, optimizing the feature subset for classification of network attacks.

### Dataset: UNSW-NB15
- **Training Set**: 175,341 records
- **Testing Set**: 82,332 records
- **Features**: 36 network traffic features
- **Classes**: Normal traffic and 9 attack types (DoS, Worms, Backdoors, Fuzzers, etc.)
- **Target**: Binary classification (0 = Normal, 1 = Attack)

### Key Features

#### Genetic Algorithm Components:
- **Chromosome Encoding**: Binary strings representing feature selection
  - `1` = Feature included
  - `0` = Feature excluded
- **Fitness Function**: Classification accuracy using Random Forest Classifier
- **Selection**: Tournament/Roulette wheel selection of best individuals
- **Crossover**: Single-point crossover for genetic recombination
- **Mutation**: Bit-flip mutation for genetic diversity

#### Implementation Details:
```python
# Key Parameters (can be adjusted for experiments)
- Population Size: Variable (e.g., 50, 100, 200)
- Number of Generations: Variable (e.g., 20, 50, 100)
- Crossover Rate: ~0.8
- Mutation Rate: ~0.01-0.05
- Classifier: Random Forest (n_estimators=100)
```

### Experiments Conducted
Three experiments were performed varying:
1. **Population Size**: Testing 50, 100, and 200 individuals
2. **Crossover Type**: Single-point vs. multi-point crossover
3. **Mutation Rate**: Testing rates of 0.01, 0.03, and 0.05

### Results
| Experiment | Population Size | Crossover Type | Mutation Rate | Best Accuracy | Features Selected |
|------------|----------------|----------------|---------------|---------------|-------------------|
| 1          | 50             | Single-point   | 0.01          | TBD           | TBD               |
| 2          | 100            | Single-point   | 0.03          | TBD           | TBD               |
| 3          | 200            | Multi-point    | 0.05          | TBD           | TBD               |

### How to Run
```bash
# Install required libraries
pip install numpy pandas scikit-learn

# Run the notebook
jupyter notebook GeneticAlgorithm.ipynb

# Or use Google Colab
# Upload the notebook and dataset files to Colab
```

---

## 📊 Question 2: Multi-Variant Linear Regression

### Overview
Custom implementation of Multi-Variant Linear Regression with Gradient Descent from scratch (no ML libraries for the model). Predicts daily productivity based on personal routine factors.

### Dataset: 20-Day Personal Routine
Custom-created dataset with the following features:

#### Independent Variables (X):
- **Sleep Hours** (1-10): Hours of sleep per night
- **Food Rank** (1-10): Quality/healthiness of food consumed
- **Working Hours** (1-10): Hours spent working
- **Health Rank** (1-10): Overall health condition rating
- **Mood Rank** (1-10): Mood quality (inverse of stress/tension)

#### Dependent Variable (y):
- **Productivity Rank** (1-10): Daily productivity level

### Mathematical Model

The regression equation:
```
y = m₁·x₁ + m₂·x₂ + m₃·x₃ + m₄·x₄ + m₅·x₅ + c
```

Where:
- `y` = Productivity Rank (target)
- `x₁` to `x₅` = Independent variables
- `m₁` to `m₅` = Coefficients (weights)
- `c` = Intercept (bias)

### Gradient Descent Implementation

#### Loss Function (Mean Squared Error):
```python
loss = (1/m) * Σ(y_pred - y_actual)²
```

#### Parameter Updates:
```python
# For each coefficient
m_i = m_i - (2/m) * learning_rate * Σ(error * x_i)

# For intercept
c = c - (2/m) * learning_rate * Σ(error)
```

#### Hyperparameters:
- **Learning Rate**: 0.001
- **Number of Epochs**: 1000
- **Initialization**: Random values for all parameters

### Features Implemented

#### 1. Exploratory Data Analysis (EDA)
- Statistical summary of all variables
- Distribution analysis
- Outlier detection

#### 2. Data Visualization
- **Scatter Plots**: Original data for each feature vs. productivity
- **Correlation Heatmap**: Shows relationships between all variables
- **Pair Plots**: Comprehensive pairwise relationships

#### 3. Model Training
- Gradient descent implementation from scratch
- Parameter tracking across epochs
- Loss calculation at each iteration

#### 4. Training Visualizations
- **Coefficient Evolution**: How each coefficient changes over epochs
- **Intercept Evolution**: Convergence of the bias term
- **Loss Curve**: Epoch vs. Loss graph showing convergence
- **Best Fit Line**: Visual representation of the learned model

### How to Run
```bash
# Install required libraries
pip install numpy pandas matplotlib seaborn

# Run the notebook
jupyter notebook Multi-Variant_Linear_Regression.ipynb
```

---

## 🛠️ Technologies Used

- **Python 3.x**
- **NumPy**: Numerical computations and array operations
- **Pandas**: Data manipulation and analysis
- **Matplotlib**: Data visualization
- **Seaborn**: Statistical visualizations
- **Scikit-learn**: Random Forest classifier (for GA fitness evaluation only)
- **Jupyter Notebook**: Interactive development environment

---

## 📈 Key Learnings

### Genetic Algorithm
1. Feature selection significantly impacts model performance
2. Balance between exploration (mutation) and exploitation (selection)
3. Population diversity prevents premature convergence
4. Trade-off between number of features and accuracy

### Gradient Descent
1. Learning rate selection is critical (too high = divergence, too low = slow convergence)
2. Feature scaling can improve convergence speed
3. Visualization helps understand optimization process
4. MSE is sensitive to outliers

---

## 🔍 Insights & Findings

### Question 1 (Genetic Algorithm)
- Optimal feature subset reduces dimensionality while maintaining accuracy
- Larger populations provide better exploration but increase computation time
- Mutation rate affects convergence speed and solution quality
- Random Forest as fitness function provides robust evaluation

### Question 2 (Linear Regression)
- **Most Influential Factors**: [Based on correlation analysis]
  - Sleep hours show [positive/negative] correlation with productivity
  - Mood rank demonstrates [strong/weak] relationship
  - Working hours exhibit [linear/non-linear] patterns
  
- **Model Performance**:
  - Convergence achieved within [X] epochs
  - Final loss: [Value]
  - Model successfully captures productivity patterns

---

## 📝 Implementation Choices

### Genetic Algorithm
- **Fitness Function**: Classification accuracy chosen for interpretability and direct optimization goal
- **Classifier**: Random Forest for robustness and handling non-linear relationships
- **Encoding**: Binary encoding for simplicity and direct feature mapping

### Linear Regression
- **Loss Function**: MSE chosen for its mathematical properties and gradient computation
- **Optimization**: Batch gradient descent for stable convergence
- **Visualization**: Comprehensive plots for understanding learning dynamics

---

## 🚀 Future Improvements

### Genetic Algorithm
- [ ] Implement elitism to preserve best solutions
- [ ] Add adaptive mutation rates
- [ ] Try different selection strategies (tournament, rank-based)
- [ ] Experiment with multi-objective optimization
- [ ] Compare with other feature selection methods (RFE, LASSO)

### Linear Regression
- [ ] Implement regularization (L1/L2)
- [ ] Add mini-batch or stochastic gradient descent
- [ ] Feature scaling/normalization
- [ ] Cross-validation for better generalization
- [ ] Compare with polynomial regression
- [ ] Add confidence intervals for predictions

---

## 📖 References

### Base Paper (Question 1):
- **Title**: "An Evolutionary Approach to Intrusion Detection System using Genetic Algorithm"
- **Dataset**: UNSW-NB15 Network Intrusion Dataset

### Learning Resources:
- Genetic Algorithms: Holland, J. H. (1992). "Adaptation in Natural and Artificial Systems"
- Gradient Descent: Goodfellow, I., et al. (2016). "Deep Learning" - Chapter 4
- UNSW-NB15 Dataset: Moustafa & Slay (2015)

---

## 👥 Team Members

[Hassan Younas] - [21I-1788]  
[Arslan Shabbir] - [21I-1739]

---

## 📄 License

This project is part of an academic assignment. Please refer to your institution's academic integrity policy before using this code.

---

## 🙏 Acknowledgments

- Institution: [FAST National University]
- Course: Artificial Intelligence

---

## 📧 Contact

For questions or discussions about this project:
- Email: [P.hassan.ph@gmail.com]
- GitHub: [@Hassan-Younas18](https://github.com/Hassan-Younas18)

---

## ⚠️ Academic Integrity Notice

This repository is made public for portfolio purposes. If you are a student taking a similar course:
- Do NOT copy this code for your assignments
- Use it only as a learning reference
- Understand the concepts and implement your own solution
- Plagiarism violates academic integrity policies

**Remember**: The goal is to learn, not just to submit!

---

## 🌟 Star This Repository

If you found this project helpful or interesting, please consider giving it a ⭐!

---

*Last Updated: February 2026*
