# Improved Conflict-Based Search (ICBS) for Multi-Agent Path Finding

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Heuristics Implemented](#heuristics-implemented)
- [Collision Resolution Strategies](#collision-resolution-strategies)
- [Installation](#installation)
- [Usage](#usage)

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

### Usage

Run experiments using the run_experiments.py script with appropriate arguments.
Command Syntax

```bash
    python3 run_experiments.py --instance <instance_file> --solver <solver_type> --h <heuristic_type> --r <repeats> [--disjoint]
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

Summary

    Heuristic Efficiency: h=0 ≤ h(CG) ≤ h(DG) ≤ h(WDG). Better heuristics reduce the number of nodes expanded and generated.
    WDG Performance: Although more computationally intensive per node, WDG performs exceptionally well on larger input maps.

Resources

This project is based on the following research:

    Improved Heuristics for Multi-Agent Path Finding with Conflict-Based Search

    Jiaoyang Li, Adi Felner, Eduard Boyarski, Hao Ma, Sven Koenig. In IJCAI-19, 2019.

    CBSH2-RTC Repository

    GitHub Repository
