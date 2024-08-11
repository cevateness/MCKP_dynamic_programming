
# Multi-Criteria Knapsack Problem (MCKP) Project

## Introduction
The Multi-Criteria Knapsack Problem (MCKP) is a sophisticated extension of the classic knapsack problem, where multiple, often conflicting, objectives must be considered simultaneously. This problem is pertinent to a wide array of real-world applications, such as resource allocation, budget management, and project selection, where decision-makers must balance diverse criteria to achieve optimal outcomes. The complexity of MCKP arises from the necessity to navigate the trade-offs between these conflicting objectives while adhering to given constraints, such as capacity limitations.

This project focuses on exploring and comparing different solution approaches for the MCKP, specifically targeting scenarios with two conflicting objectives and two capacity constraints. Scalarization methods such as the Weighted Sum approach and the Tchebycheff method are implemented alongside a dynamic programming algorithm with an extension to handle multiple capacity constraints. The objective is to assess computational efficiency and quality of solutions provided by these methods. By doing so, this project aims to analyze the performance of scalarization methods and compare them with the efficient frontier found by the dynamic programming approach.

## Literature Review
The literature on MCKP spans a wide range of approaches, from heuristic and evolutionary algorithms to dynamic programming and branch-and-bound techniques. Key studies include:

- **Klamroth and Wiecek (2000)**: Investigate dynamic programming-based approaches for the integer multi-criteria knapsack problem, proposing various strategies to improve computational efficiency.
- **Erlebach, Kellerer, and Pferschy (2002)**: Focus on heuristic and approximation algorithms for multi-objective knapsack problems, analyzing their performance in different scenarios.
- **Captivo et al. (2003)**: Propose a labeling algorithm to generate all efficient solutions for bi-criteria 0-1 knapsack problems.
- **Kumar and Banerjee (2006)**: Analyze a multi-objective evolutionary algorithm, highlighting its benefits in exploring the solution space and finding Pareto optimal solutions.
- **Bazgan, Hugot, and Vanderpooten (2009)**: Present efficient algorithms based on dynamic programming and branch-and-bound techniques for the 0-1 multi-objective knapsack problem.
- **Florios, Mavrotas, and Diakoulaki (2010)**: Explore hybrid algorithms combining mathematical programming and evolutionary algorithms for multi-objective, multi-constraint knapsack problems.
- **Lust and Teghem (2012)**: Review various approaches to multi-objective multi-dimensional knapsack problems and propose a new method integrating dynamic programming with other optimization techniques.
- **Figueira et al. (2013)**: Improve dynamic programming algorithms for the bi-objective knapsack problem, focusing on handling larger and more complex instances.
- **Rong and Figueira (2014)**: Apply dynamic programming algorithms to the bi-objective integer knapsack problem, introducing new optimization strategies.

## Problem Definition
MCKP is an optimization problem encountered in many real-world applications where multiple conflicting objectives need to be optimized simultaneously. The main goal of MCKP is to find a set of solutions that maximize a series of different criteria under given constraints. In this project, there will be two different criteria to maximize, with constraints based on capacity limitations, interpreted as volume and weight.

## Mathematical Model
The mathematical model of MCKP can be formulated as follows:

$$
\text{Max} \sum_{i=1}^{n} p_{ij} x_j \text{ for } i = \{1, 2\}
$$

$$
\sum_{j=1}^{n} w_{ij} x_j \le c_i \text{ for } i = \{1, 2\}
$$

$$
x_j \in \{0, 1\} \forall j
$$

Where:
- $x$ represents the decision variables, and each $x_j$ can take a value of 0 or 1.
- $P \in \mathbb{R}^{k \times n}$ is a matrix representing $k$ criteria showing the utilities taken from each item for each criterion.
- $W \in \mathbb{R}^{m \times n}$ is the capacity usage constraint matrix for $m$ different capacity limitations.
- $c \in \mathbb{R}^m$ represents the capacity of each limitation.

The objective functions usually aim to maximize the total value of the items included in the knapsack, while the constraints ensure that the total weight of the knapsack does not exceed a certain limit. The goal is to find the best possible solutions considering all these criteria and present these solutions to the decision-makers (DMs).

## Solution Approach
In this project, two different approaches are selected to solve the MCKP: the Weighted Sum method and the Tchebycheff method.

### Weighted Sum Approach
The Weighted Sum method combines multiple objectives into a single objective function by assigning a weight to each objective. For this project, the weights are selected evenly (0.5 and 0.5), allowing us to balance all objectives and provide a unique solution according to the weighted objective.

### Tchebycheff Method – Min. Max. Distance to the Ideal Point
The Tchebycheff method is a widely used approach in multi-objective optimization that focuses on minimizing the worst distance from the ideal point of each objective. The ideal point is obtained by solving each objective separately for the same problem and combining the best solutions for each objective. The mathematical model is updated as follows:

- $t$: A new variable representing the maximum distance from the ideal point, $I_i$, for each objective.
- The objective function changes to $t$, which we want to minimize.
- A new constraint is added to calculate the maximum Tchebycheff distance to the ideal point:

$$
t \geq I_i - \sum_{j=1}^{n} P_{ij} x_{ij} \ \forall i 
$$

## Alternative Solution Methods
For the solution of the MCKP, in addition to the Weighted Sum and Min Max distance to the ideal solution, one of the dynamic programming approaches presented by Klamroth and Wiecek (2000) is implemented. 

### Dynamic Programming Approach
This approach extends dynamic programming to handle multiple capacity constraints. The problem is solved by calculating the repetitive function $G$, which represents the maximum benefit obtainable from a given capacity with selected items.
