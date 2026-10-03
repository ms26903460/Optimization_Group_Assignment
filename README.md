# CVRP Optimization Using Exact and Heuristic Methods

## Project Overview

This project solves the **Capacitated Vehicle Routing Problem (CVRP)** using two optimization approaches:

* **Exact Method:** Integer Linear Programming (ILP)
* **Heuristic Method:** Genetic Algorithm (GA)

The objective is to minimize the total distance travelled by a fleet of vehicles while satisfying customer demands, vehicle capacity, and routing constraints.

## Dataset

Two datasets were used in the implementation.

### Synthetic Dataset

A randomly generated synthetic CVRP dataset was used initially to test and validate the implementation.

The synthetic dataset contains:

- Randomly generated customer coordinates
- Randomly generated customer demands
- A fixed depot
- Vehicle capacity constraints

The synthetic data is generated reproducibly using a fixed random seed.

### Real-World Benchmark Dataset

The main experiment uses the **A-n32-k5** CVRP benchmark instance from the Capacitated Vehicle Routing Problem Library (CVRPLIB).

Dataset details:

- **Instance:** A-n32-k5
- **Nodes:** 32
- **Customers:** 31
- **Vehicles:** 5
- **Vehicle capacity:** 100
- **Distance type:** EUC_2D
- **Known benchmark value:** 784

### Dataset Source

The A-n32-k5 dataset was obtained from **CVRPLIB**:
https://galgos.inf.puc-rio.br/cvrplib/en/instances/1

CVRPLIB provides standard benchmark instances for CVRP and other vehicle routing problems.

## Methods

### Integer Linear Programming (ILP)

ILP was implemented as the exact optimization approach.

The formulation includes:

- Binary routing variables
- Customer visit constraints
- Vehicle constraints
- Vehicle capacity constraints
- Subtour elimination constraints
- Total route distance minimization

The ILP model was solved using the **CBC solver through PuLP**.

### Genetic Algorithm (GA)

A Genetic Algorithm was implemented as the heuristic approach.

The GA includes:

- Random permutation-based initial population
- Tournament selection
- Order Crossover (OX)
- Swap and inversion mutation
- Elitism
- Capacity-based route splitting
- 2-opt local search for route improvement

A fixed random seed was used to improve reproducibility.

## Results

| Method            | Distance |  Runtime | Benchmark Gap | Valid |
| ----------------- | -------: | -------: | ------------: | ----- |
| ILP               |   1013.0 | 899.51 s |        29.21% | Yes   |
| Genetic Algorithm |    858.0 |   3.74 s |         9.44% | Yes   |

The Genetic Algorithm obtained a solution closer to the benchmark value while requiring substantially less runtime than the ILP experiment.

## Technologies

* Python
* Jupyter Notebook
* PuLP 
* NumPy
* Pandas
* Matplotlib

## Contributors

- **Nadeesha**  
  - Integer Linear Programming (ILP)
  - Real Word Dataset Validation

- **Irsha**  
  - Genetic Algorithm (GA) 
  - Real Word Dataset Validation
