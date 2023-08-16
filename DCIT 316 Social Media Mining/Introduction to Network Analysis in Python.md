# NetworkX API Basics
Allows manipulation, analysis, and modelling of graph data
```python
import networkx as nx
G = nx.Graph() # Initializes graph
G.add_nodes_from([1, 2, 3]) # Adds nodes
G.nodes() # Returns [1, 2, 3], a list of nodes

G.add_edge(1,2) # Adds an edge b/n node 1 and 2
G.edges() # Returns [(1, 2)], a list of tuples
```
- Metadata can be added to the nodes in the graph, providing extra information
```python
G.node[1]['Label'] = 'blue'
G.nodes(data=True) # Returns [(1, {'label': 'blue'}), (2, {}), (3, {})]
```
- Provides drawing functionality
```python
nx.draw(G)
import matplotlib.pyplot as plt
plt.show() # Displays a node-link diagram of the graph
```

# #