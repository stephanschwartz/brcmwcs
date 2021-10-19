### Online Supplement of

# Rooted Maximum Weight Connected Subgraphs with Balancing and Capacity Constraints

#### Ralf Borndörfer, Stephan Schwartz, and William Surau

Zuse Institute Berlin, Takustr 7, 14195 Berlin

---

This online supplement provides instances and detailed results of the computational experiments conducted for the paper "Rooted Maximum Weight Connected Subgraphs with Balancing and Capacity Constraints". A preprint is available as [technical report](https://opus4.kobv.de/opus4-zib/frontdoor/index/index/docId/8442) published by Zuse Institute Berlin, 2021.

## Instances
The instances stem from a [transit network generator](https://github.com/stephanschwartz/transit_network_generator) used in [this paper](https://opus4.kobv.de/opus4-zib/frontdoor/index/index/docId/8442). These networks are edge weighted with a length and a traffic value. We transform the transit networks into node weighted graphs. The weight of a node represents the length of the corresponding edge. As a root we chose a random node and the color of a node depends on whether the traffic value is higher or lower then the traffic at the root.

We constructed 5 such network instances where the number of nodes ranges from 563 to 569 and the number of edges from 845 to 885. For each network, we consider 9 different profits: 3 are actual reduced costs from the pricing problem from TODO\cite{borndorfer2021vertex}, 3 are distributed uniformly at random in the interval [-1,1], and 3 are based on the normal distribution to thin out extreme profits. For one instance per profit class, we also used a random partition into red and blue vertices. Finally, we consider 4 different upper weight bounds that lie between 40% and 75% of the graph diameter, and are motivated by our application. The lower bounds were set to half of the upper bounds but showed no effect in any computation. Altogether we have 5 * 12 * 4 = 240 test instances.
The instances are encoded as follows (examples: i-124, i-37c1):

|              |                                     |
| ------------ | ----------------------------------- |
| 1st digit    | which network (1-5)                 |
| 2nd digit    | which profits (1-9)                 |
| c (optional) | variant with random color partition |
| 3rd digit    | which weight bounds (1-4)           |


Our instances are provided as .graphml files. The graph has attributes "root" and "delta" and can be loaded in Python using networkx as follows:

```
import networkx as nx
path_to_file = 'instances/i-11'
graph = nx.read_graphml(path_to_file, node_type=int)
root = int(graph.graph['root'])
delta = graph.graph['delta']
```

