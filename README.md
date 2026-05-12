# Spark RDD Connected Components - CCF Algorithm

## Description

This project implements the Connected Component Finder (CCF) algorithm using Apache Spark RDDs.

The goal is to compute the connected components of an undirected graph through an iterative propagation of the smallest node identifier. The implementation is based only on the Spark RDD API, without using GraphFrames or GraphX.

## Objective

The objective of this project is to:

- Represent a graph using Spark RDDs
- Transform directed edges into undirected edges
- Implement a connected components algorithm
- Use iterative processing with Spark transformations and actions
- Compare a basic implementation with an optimized version
- Understand distributed graph processing with RDDs

## Technologies Used

- Python
- PySpark
- Apache Spark
- RDD API
- Jupyter Notebook / Zeppelin Notebook

## Algorithm Principle

The CCF algorithm is based on the propagation of the smallest identifier inside each connected component.

For each node, the algorithm compares the node identifier with the identifiers of its neighbors. The smallest identifier is progressively propagated through the graph until convergence.

At the end, all nodes belonging to the same connected component are associated with the same minimum identifier.

## Implemented Versions

### 1. Basic version using `groupByKey`

This version groups all neighbors of each node, then propagates the minimum identifier to the node and its neighbors.

Main operations:

- `groupByKey`
- `flatMap`
- `distinct`

This version is easier to understand but can be less efficient because `groupByKey` may generate more data movement.

### 2. Improved version using `reduceByKey` and `join`

This version avoids grouping all values directly and uses more efficient Spark transformations.

Main operations:

- `map`
- `union`
- `reduceByKey`
- `join`
- `filter`


