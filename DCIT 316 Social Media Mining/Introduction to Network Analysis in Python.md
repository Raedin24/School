# NetworkX API Basics
Allows manipulation, analysis, and modelling of graph data
```python
import networkx as nx
G = nx.Graph() # Initializes graph
G.add_nodes_from([1, 2, 3]) # Adds nodes
G.nodes() # Returns [1, 2, 3]

G.add_edge(1,2) # Adds an edge b/n node 1 and 2
G.edges() # Returns [(1, 2)]
```
- Metadata can be added to the nodes in the graph, providing extra information
```python
G.node[1]['Label']
```