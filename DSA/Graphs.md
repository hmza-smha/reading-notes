# Graphs

## A graph is a non-linear data structure that can be looked at as a collection of ```vertices```

###  Directed vs Undirected

- Undirected Graphs

An Undirected Graph is a graph where each edge is undirected or bi-directional. 

- Directed Graphs (Digraph)

A Directed Graph also called a Digraph is a graph where every edge is directed.

Each node is directed at another node with a specific requirement of what node should be referenced next.

### Complete vs Connected vs Disconnected

- Complete Graphs
A complete graph is when all nodes are connected to all other nodes.

- Connected
A connected graph is graph that has all of vertices/nodes have at least one edge.

- Disconnected
A disconnected graph is a graph where some vertices may not have edges.

### Acyclic vs Cyclic

- Acyclic Graph

An acyclic graph is a directed graph without cycles.

- Cyclic Graphs

A Cyclic graph is a graph that has cycles.

***NOTE:*** *A cycle is when a node can be traversed through and potentially end up back at itself.*


## Graph Representation

1. Adjacency Matrix
2. Adjacency List

- Adjacency Matrix
An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix

- Adjacency List

An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

### Weighted Graphs
A weighted graph is a graph with numbers assigned to its edges. These numbers are called weights.


### Traversals

- Breadth First

```
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)

    return nodes;
```


### Real World Uses of Graphs

- GPS and Mapping
- Driving Directions
- Social Networks
- Airline Traffic
- Netflix uses graphs for suggestions of products