


```c++
  $\theta$ = 0; $\beta$ = 0.2;

  // contracting degree-1 nodes
  vector<Neighbor> closest;
  g.contract(closest, true);

  // Building tree hierarchy
  vector<CutIndex> ci;
  g.create_cut_index(ci, $\beta$, $\theta$);

  // reset if degree-1 nodes are contracted
  g.reset();

  // initializing shortcut graph and tree labeling
  ContractionHierarchy ch;
  g.initialize(ch, ci, closest);
  ContractionIndex con_index(ci, closest);
```
