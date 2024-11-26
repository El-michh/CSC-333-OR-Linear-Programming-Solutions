 Linear Programming Problems  

This project demonstrates solving various Linear Programming (LP) problems using Python and the `PuLP` library. The problems focus on optimizing objectives like maximizing profit, revenue, or production, and minimizing costs under specified constraints. The solutions provide practical examples of how LP can be applied in real-world scenarios.  

Objectives  

The primary goals of this project are:  
1. To solve real-world optimization problems using linear programming techniques.  
2. To provide reusable Python scripts for solving LP problems efficiently.  
3. To offer clear, step-by-step instructions to run the scripts and interpret the results.  

 Problem Descriptions  

Here is a brief overview of the problems tackled in this project:  

1. Maximizing Profit for a Factory  
   Optimize the production of two products, A and B, to maximize profit under machine time and raw material constraints.  

2. Minimizing Cost for a Manufacturer  
   Determine production levels for products X and Y to minimize costs within labor and material availability.  

3. Maximizing Production with Multiple Resources  
   Optimize the output of two products given constraints on labor, material, and machine time.  

4. Maximizing Revenue from Sales  
   Allocate advertising budget and production resources to maximize revenue.  

5. Resource Allocation for Two Projects  
   Distribute labor hours and capital between two projects to maximize profit.  

6. Production Planning for a Bakery  
   Plan the production of chocolate and vanilla cakes to maximize profit while adhering to time and material constraints.  

7. Minimizing Cost for a Transport Company  
   Allocate trips for two types of vehicles to minimize operational costs within fuel and driver time limits.  

8. Maximizing Revenue from Two Products  
   Determine the production of two products to maximize revenue under labor, raw material, and machine time constraints.  

9. Advertising Campaign Budget Allocation  
   Allocate a fixed advertising budget across two campaigns to maximize reach.  

10. Meal Planning for a School Cafeteria  
    Plan weekly meal schedules to maximize revenue while considering ingredient availability.  

---
 Solution Approach  

1. Define Decision Variables  
   Represent key quantities (e.g., units of products, budgets, trips) as decision variables.  

2. Formulate the Objective Function  
   Define the goal, such as maximizing profit or minimizing cost, in terms of the decision variables.  

3. Set Constraints  
   Incorporate real-world limits (e.g., budget, material, time) as mathematical constraints.  

4. Solve Using `PuLP`  
   Utilize Python’s `PuLP` library to define, solve, and extract results from LP models.  

 How to Run the Code  
 
 Prerequisites  

1. Install Python  
   Ensure Python 3.7 or newer is installed.  

2. Install Required Libraries  
   Install the `PuLP` library:  
   ```bash  
   pip install pulp  
   ```  

 Running the Scripts  

1. Download the Repository  
   Clone or download the project repository to your local machine.  

2. Execute a Script  
   Each problem is implemented in a separate Python file (e.g., `problem_1.py`). To run a specific problem:  
   ```bash  
   python problem_1.py  
   ```  
   Replace `problem_1.py` with the filename of the desired problem.  

3. View Results  
   The output will display optimal values for decision variables and the optimized objective function.  

---

 Example: Problem 1 - Maximizing Profit for a Factory  

 Problem Description:  

Goal: Maximize profit from producing two products (A and B).  
Resources: Limited machine time (12 hours/day) and raw materials (8 units/day).  
Profit per unit: N3 for product A and N4 for product B.  

 Mathematical Model:  
- Decision Variables:  
  \( x_A \): Units of product A, \( x_B \): Units of product B.  
- Objective Function:  
  Maximize \( Z = 3x_A + 4x_B \).  
- Constraints:  
  1. \( 2x_A + 3x_B \leq 12 \) (Machine time)  
  2. \( x_A + 2x_B \leq 8 \) (Raw material)  
  3. \( x_A, x_B \geq 0 \)  

 Python Implementation:  
```python  
from pulp import LpMaximize, LpProblem, LpVariable  

# Define the LP problem  
problem = LpProblem("Maximize_Profit", LpMaximize)  

# Decision variables  
xA = LpVariable("xA", lowBound=0)  # Units of Product A  
xB = LpVariable("xB", lowBound=0)  # Units of Product B  

# Objective function  
problem += 3 * xA + 4 * xB, "Total Profit"  

# Constraints  
problem += 2 * xA + 3 * xB <= 12, "Machine Time Constraint"  
problem += xA + 2 * xB <= 8, "Raw Material Constraint"  

# Solve the problem  
problem.solve()  

# Output the results  
print("Optimal production of Product A:", xA.varValue)  
print("Optimal production of Product B:", xB.varValue)  
print("Maximum Profit:", problem.objective.value())  
```  

### Output:  
```
Optimal production of Product A: 4.0  
Optimal production of Product B: 2.0  
Maximum Profit: 20.0  
```  
