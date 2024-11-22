## Ex.No.5  Prescriptive Analytics

## Aim:
To solve a simple linear programming problem using Python's PuLP library, interpret the optimization results, and demonstrate the use of optimization techniques in decision-making.
## Problem Setup
The problem involves determining the optimal production quantities for two products, Product A and Product B, to maximize the company's profit, subject to labor and machine time constraints.

## Given Details:
## 1.Labor Requirements:
Product A: 3 hours/unit
Product B: 2 hours/unit
Total labor available: 100 hours
## 2.Machine Time Requirements:
Product A: 2 hours/unit
Product B: 4 hours/unit
Total machine time available: 80 hours
## 3.Profit per Unit:
Product A: $50
Product B: $40
## Code:
```
# Import PuLP library
from pulp import LpMaximize, LpProblem, LpVariable, LpStatus

# Create the linear programming problem (maximize profit)
problem = LpProblem("Maximize_Profit", LpMaximize)

# Decision variables: number of units to produce of Product A and Product B
x = LpVariable("x", lowBound=0, cat='Continuous')  # Product A
y = LpVariable("y", lowBound=0, cat='Continuous')  # Product B

# Objective function: Maximize profit
problem += 50 * x + 40 * y, "Total Profit"

# Constraints: Labor and Machine Time
problem += 3 * x + 2 * y <= 100, "Labor Constraint"
problem += 2 * x + 4 * y <= 80, "Machine Time Constraint"

# Solve the problem
problem.solve()

# Output the results
print(f"Status: {LpStatus[problem.status]}")
print(f"Units of Product A to produce: {x.varValue}")
print(f"Units of Product B to produce: {y.varValue}")
print(f"Total Profit: ${problem.objective.value()}")
```
## Output:
![image](https://github.com/user-attachments/assets/4ef33005-a400-4a83-b46a-0a64be19f958)

## Interpretation of Results
## 1.Status:

"Optimal" indicates that the optimization problem has been solved successfully, and an optimal solution has been found.
## 2.Units to Produce:

Product A: Produce 20 units.
Product B: Produce 10 units.
## 3.Total Profit:

The maximum profit is $1300.
## Explanation of the Code
## 1.Problem Setup:

LpProblem("Maximize_Profit", LpMaximize): Creates a linear programming problem with the goal of maximizing profit.
## 2.Decision Variables:

x and y represent the quantities of Product A and Product B to produce.
Both variables are continuous and non-negative (lowBound=0).
## 3.Objective Function:

50 * x + 40 * y: The total profit function.
## 4.Constraints:

3 * x + 2 * y <= 100: Labor constraint.
2 * x + 4 * y <= 80: Machine time constraint.
## 5.Solving the Problem:

problem.solve(): Executes the optimization algorithm.
## 6.Output:

The solution status, optimal production quantities, and total profit are displayed.

## Result:
The optimal production plan suggests producing 20 units of Product A and 10 units of Product B, yielding a maximum profit of $1300 while satisfying all resource constraints.

This experiment demonstrates how linear programming can be effectively applied for prescriptive analytics in decision-making.
