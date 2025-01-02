


## Preprocessing
```c++
// reading the graph weights

graph_file = ../Sample Input/g.txt

Graph g;
ifstream ifs(graph_file);
read_graph(g, ifs);
ifs.close();

// setting parameters 
theta = 0; beta = 0.2;

// contracting degree-1 nodes
vector<Neighbor> closest;
g.contract(closest, true);

// Building tree hierarchy
vector<CutIndex> ci;
g.create_cut_index(ci, beta, theta);

// reset if degree-1 nodes are contracted
g.reset();

// initializing shortcut graph and tree labeling
ContractionHierarchy ch;
g.initialize(ch, ci, closest);
ContractionIndex con_index(ci, closest);
```

## customization
```c++
// weight metric
vector<Edge> edges;
g.get_edges(edges);

// customising shortcut graph
g.customise_shortcut_graph(ch, con_index, edges);
//customising tree labeling
g.customise_tree_labeling(ch, con_index);

// reset before second iteration
g.reset(ch, con_index);
```

## Query
```c++
vector<NodeID> path = g.query(ch, con_index, s, t);
```
