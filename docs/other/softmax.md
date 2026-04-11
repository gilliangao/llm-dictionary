# Softmax

## What is Softmax?
Softmax is a function that converts a list of numbers (scores) into probabilities. It takes any set of numbers and transforms them so they add up to 1, making them suitable for representing probabilities or confidence levels.

## The Softmax Equation

**Basic Version:**
```
softmax(x_i) = exp(x_i) / Σ exp(x_j)
```

**With Temperature Scaling (commonly used in ML):**
```
σ(z)_i = e^(z_i/T) / Σ(j=1 to K) e^(z_j/T)
```

where:
- `z_i` is the individual score we're converting
- `T` is the temperature parameter (controls sharpness)
- `exp()` is the exponential function (e raised to the power)
- `Σ e^(z_j/T)` is the sum of all exponentials for all scores

## Understanding Temperature (T)

The temperature parameter controls how "confident" or "spread out" the probabilities are:

- **T = 1**: Standard softmax, normal probability distribution
- **T < 1 (e.g., 0.5)**: Temperature is "cold" - probabilities become more extreme, favoring the highest scores
- **T > 1 (e.g., 2)**: Temperature is "hot" - probabilities become more uniform, softer distribution

**Example:**
- Scores: [2, 1, 0]
- T=0.5 (cold): Probabilities become [0.88, 0.11, 0.01] - very confident
- T=1 (normal): Probabilities become [0.66, 0.24, 0.10] - balanced
- T=2 (hot): Probabilities become [0.54, 0.33, 0.13] - softer, more uniform


## Simple Explanation

**Step 1: Exponentiate each score**
- Take each number and raise e (≈2.718) to that power
- This makes larger numbers much larger and smaller numbers much smaller

**Step 2: Sum all the exponentials**
- Add up all the numbers from Step 1

**Step 3: Divide each exponent by the sum**
- Each exponential score divided by the total
- Result: all numbers between 0 and 1, adding up to exactly 1

## Real-World Analogy

Imagine you have 3 students competing for a prize:
- They scored 8, 6, and 2 on a test
- Softmax converts these scores to: 92% chance for the first, 7% for the second, 1% for the third
- The better scores get higher probabilities (but not just proportional to the raw scores)

## Why Use Softmax?

1. **Converts scores to probabilities** - Makes model outputs interpretable
2. **Emphasizes differences** - Good scores become very likely, poor scores become very unlikely
3. **Differentiable** - Can be used with gradient-based optimization in neural networks

## Example

Scores: [2, 1, 0.1]

- exp(2) ≈ 7.39, exp(1) ≈ 2.72, exp(0.1) ≈ 1.11
- Sum = 7.39 + 2.72 + 1.11 = 11.22
- Softmax: [7.39/11.22, 2.72/11.22, 1.11/11.22] ≈ [0.66, 0.24, 0.10]
- These now represent probabilities: 66%, 24%, 10%
