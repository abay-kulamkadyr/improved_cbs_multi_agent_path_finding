# Improved Conflict-Based Search (ICBS) for Multi-Agent Path Finding

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Heuristics Implemented](#heuristics-implemented)
- [Collision Resolution Strategies](#collision-resolution-strategies)
- [Installation](#installation)
- [Usage](#usage)
- [Experimental Results](#experimental-results)
- [Project Structure](#project-structure)
- [Resources](#resources)
- [Contact](#contact)
- [License](#license)

## Overview

The **Improved Conflict-Based Search (ICBS)** project offers an optimal solution to the **Multi-Agent Path Finding (MAPF)** problem using an enhanced version of the **Conflict-Based Search (CBS)** algorithm. By integrating advanced heuristics and collision resolution strategies, ICBS significantly improves the efficiency and scalability of solving MAPF instances.

## Features

- **Optimal MAPF Solver**: Guarantees finding the shortest possible paths for all agents without conflicts.
- **Advanced Heuristics**: Incorporates multiple heuristic strategies to guide the high-level search.
- **Efficient Collision Resolution**: Implements both standard and disjoint splitting methods.
- **Performance Metrics**: Evaluates algorithms based on runtime, expanded nodes, and generated nodes.
- **Visualization**: Provides simulation capabilities to visualize agent paths and collisions.

## Heuristics Implemented

1. **Prioritize Cardinal Conflicts**: Focuses on resolving inevitable conflicts first.
2. **Minimum Vertex Cover of Cardinal Conflict Graph (CG)**: Utilizes graph theory to minimize conflicts.
3. **Minimum Vertex Cover of Dependency Graph (DG)**: Further optimizes conflict resolution by analyzing dependencies.
4. **Minimum Weighted Vertex Cover of Weighted Dependency Graph (WDG)**: Incorporates edge weights for more nuanced conflict management.

## Collision Resolution Strategies

- **Standard Splitting**: Traditional method to handle collisions by imposing constraints on conflicting agents.
- **Disjoint Splitting**: An alternative approach that randomly selects one agent to resolve the conflict and imposes that agent to go down that path, this is a stronger contraint and will reduce the search space.

## Installation

### Prerequisites

- **Python 3.6+**
- **Required Libraries**:
  - `matplotlib`
  - `numpy`

### Usage

Run experiments using the run_experiments.py script with appropriate arguments.
Command Syntax

    ```bash
    python run_experiments.py --instance <instance_file> --solver <solver_type> --h <heuristic_type> --r <repeats> [--disjoint]
    ```
Arguments

    --instance: Path to the input map instance file.
    --solver: MAPF solver to use (CBS or ICBS).
    --h: Heuristic to apply (options below).
    --r: Number of times to run the experiment on the instance.
    --disjoint: (Optional) Use disjoint splitting for collision resolution.

Heuristic Options (--h)

    0: Prioritizing Cardinal Conflicts
    1: Cardinal Graph (CG) Heuristic
    2: Dependency Graph (DG) Heuristic
    3: Weighted Dependency Graph (WDG) Heuristic

Example

python run_experiments.py --instance instances/test_47.txt --solver ICBS --h 2 --r 1 --disjoint

This command runs the ICBS solver on test_47.txt using the Dependency Graph heuristic, executes the experiment once, and employs disjoint splitting for collision resolution.
Experimental Results
Experiment 1: Standard Splitting
Heuristic	Running Time (s)	Expanded Nodes	Generated Nodes	Average h-values
h=0	17.72	2966	5931	0.00
h=1	12.28	1952	3903	0.10
h=2	0.25	36	71	3.20
h=3	0.99	16	31	0.61
Experiment 2: Disjoint Splitting
Heuristic	Running Time (s)	Expanded Nodes	Generated Nodes	Average h-values
h=0	6.22	655.15	1104.05	0.00
h=1	4.66	464.45	818.65	0.17
h=2	0.49	35.9	64.35	3.19
h=3	1.70	30.45	53.65	0.35

Summary

    Heuristic Efficiency: h=0 ≤ h(CG) ≤ h(DG) ≤ h(WDG). Better heuristics reduce the number of nodes expanded and generated.
    WDG Performance: Although more computationally intensive per node, WDG performs exceptionally well on larger input maps.

Project Structure

improved_cbs_multi_agent_path_finding/
├── src/
│   ├── cbs.py
│   ├── cbs_utilities.py
│   ├── common_for_search.py
│   ├── icbs.py
│   ├── mdd.py
│   ├── minimumVertexCover.py
│   ├── minimumWeightedVertexCover.py
│   ├── results.py
│   ├── run_experiments.py
│   ├── single_agent_planner.py
│   └── visualize.py
├── custominstances/
│   ├── experiment1.txt
│   ├── experiment2.txt
│   ├── test0.txt
│   ├── test2.txt
│   └── wdg_test.txt
├── instances/
│   ├── PaxHeaders.1451/
│   │   ├── exp0.txt
│   │   ├── exp1.txt
│   │   ├── exp2_1.txt
│   │   ├── exp2_2.txt
│   │   ├── exp2_3.txt
│   │   ├── exp4.txt
│   │   ├── min-sum-of-cost.csv
│   │   ├── test_1.txt
│   │   ├── ... (other test files)
│   └── ... (other instance folders)
├── README.md
└── LICENSE

Resources

This project is based on the following research:

    Improved Heuristics for Multi-Agent Path Finding with Conflict-Based Search

    Jiaoyang Li, Adi Felner, Eduard Boyarski, Hao Ma, Sven Koenig. In IJCAI-19, 2019.

    CBSH2-RTC Repository

    GitHub Repository
