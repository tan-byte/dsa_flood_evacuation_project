# 🌊 Flood-Aware Evacuation Routing Simulator

A DSA-focused graph simulation project that predicts flood spread in a city and computes the shortest safe evacuation route while avoiding locations that will be flooded before arrival.

# 🚀 Project Overview

In disaster scenarios like floods, the shortest path is not always the safest path.

This project models a city as a graph, predicts flood arrival times, and then computes an evacuation route that ensures a person never enters a flooded location.

The system works in two phases:

1. Flood Prediction

2. Safe Path Computation

# 🧠 Key Idea

First predict when each location floods, then find the shortest path that always stays ahead of the flood.

# 🏙️ City Model

## Nodes → City locations

## Edges → Roads with travel time

Each node stores:

1. Elevation

2. Flood arrival time (floodTime)

Internally, the city is represented using an Adjacency List Graph.

# 🌊 Phase 1: Flood Simulation (Prediction)

Flood spreads from river or low-lying areas to nearby locations.

## Algorithm Used

Multi-Source BFS (Breadth-First Search)

## Why BFS?

Flood spreads uniformly step-by-step

BFS efficiently computes the earliest time flood reaches each node

## Output

Each node gets a floodTime:

Node A → floods at time 0
Node B → floods at time 1
Node C → floods at time 2


## This is predictive, not real-time.

# 🚶 Phase 2: Safe Evacuation Path

A person starts at a source node and wants to reach a destination before flooding occurs.

## Algorithm Used

1. Modified Dijkstra’s Algorithm

2. Priority Queue (Min-Heap)

## Safety Rule

A node is considered unsafe if:

### arrivalTime ≥ floodTime(node)

Such paths are rejected immediately.

# Result

## The algorithm finds:

1. The shortest possible path

2. That remains safe throughout traversal

## 📊 Algorithms & Data Structures Used
## Data Structures

1. Graph (Adjacency List)

2. Queue (for BFS)

3. Priority Queue (Min-Heap)

4. HashMap / Arrays

5. Custom Node & State classes

## Algorithms

1. Multi-Source BFS

2. Dijkstra’s Algorithm (with constraints)

3. Greedy optimization

4. Time-based pruning

# ⏱️ Complexity Analysis
Operation	Time Complexity
Flood Simulation (BFS)	O(V + E)
Safe Path Finding	O(E log V)
Space Complexity	O(V + E)
