# NetworkX 

NetworkX is used to create, modify, analyse and draw graphs.

## 1. Import and create graph

```
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()     # Undirected graph
D = nx.DiGraph()   # Directed graph
```

## 2. Add nodes

```
G.add_node(1)
G.add_nodes_from([2, 3, 4])
```

## 3. Add edges

```
G.add_edge(1, 2)

G.add_edges_from([
    (1, 3),
    (2, 3),
    (3, 4)
])
```

Adding an edge automatically adds missing endpoint nodes.

## 4. Remove nodes and edges

```
G.remove_node(4)
G.remove_edge(1, 2)

G.clear()       # Remove all nodes and edges
```

## 5. Display information

```
list(G.nodes())       # Nodes
list(G.edges())       # Edges

G.number_of_nodes()   # Node count
G.number_of_edges()   # Edge count

G.degree(1)           # Degree of node 1
```

## 6. Connectivity

```
nx.is_connected(G)

nx.number_connected_components(G)

list(nx.connected_components(G))

nx.has_path(G, 1, 3)

nx.shortest_path(G, 1, 3)
```

These are primarily for undirected `Graph` objects; directed graphs have different connectivity definitions.

## 7. Draw graph

```
nx.draw(G, with_labels=True)
plt.show()
```

Save graph:

```
nx.draw(G, with_labels=True)
plt.savefig("graph.png")
plt.show()
```

## 8. Complete faculty-style program

```
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()

G.add_edges_from([
    (1, 2),
    (1, 3),
    (2, 3),
    (3, 4)
])

print(G.number_of_nodes())
print(G.number_of_edges())
print(nx.is_connected(G))
print(nx.shortest_path(G, 1, 4))

nx.draw(G, with_labels=True)
plt.show()
```

Output:

```
4
4
True
[1, 3, 4]
```

## 9. Weighted edges

```
G.add_edge(1, 2, weight=5)

nx.shortest_path(
    G, source=1, target=2, weight="weight"
)
```

Without `weight`, shortest path minimizes number of edges.

With `weight="weight"`, it minimizes total edge weight.

## Memory Tricks

|Function|Meaning|
|---|---|
|`nx.Graph()`|Undirected graph|
|`nx.DiGraph()`|Directed graph|
|`add_node()`|Add node|
|`add_edge()`|Add edge|
|`add_edges_from()`|Add many edges|
|`number_of_nodes()`|Node count|
|`number_of_edges()`|Edge count|
|`is_connected()`|Check connectivity|
|`has_path()`|Check reachability|
|`shortest_path()`|Find shortest path|
|`nx.draw()`|Draw graph|

**Faculty slides 53–60.**