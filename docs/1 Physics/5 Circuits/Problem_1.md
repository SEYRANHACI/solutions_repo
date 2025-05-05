# Problem 1




circuits  
1.1


🔹 Mathematical Concepts
1. Series Rule:
Resistors in series simply add:

𝑅
eq
=
𝑅
1
+
𝑅
2
+
⋯
+
𝑅
𝑛
R 
eq
​
 =R 
1
​
 +R 
2
​
 +⋯+R 
n
​
 
2. Parallel Rule:
Resistors in parallel combine reciprocally:

1
𝑅
eq
=
1
𝑅
1
+
1
𝑅
2
+
⋯
+
1
𝑅
𝑛
R 
eq
​
 
1
​
 = 
R 
1
​
 
1
​
 + 
R 
2
​
 
1
​
 +⋯+ 
R 
n
​
 
1
​
 
🔹 Algorithm Description (English)
Step-by-step outline:
Input: A graph 
𝐺
=
(
𝑉
,
𝐸
)
G=(V,E) with resistors as edge weights.

Identify series connections:

Look for nodes with exactly 2 neighbors (degree = 2).

Combine the two connecting resistors in series.

Identify parallel connections:

Find multiple edges between the same two nodes.

Combine them using the parallel rule.

Reduce the graph iteratively until only 2 nodes remain: the source and target.

Return the final resistance between these nodes.

import networkx as nx

def combine_parallel_resistors(resistances):
    # Combine resistances in parallel: 1/R = 1/R1 + 1/R2 + ...
    inverse_total = sum(1/r for r in resistances)
    return 1 / inverse_total if inverse_total != 0 else float('inf')

def simplify_circuit(G):
    # Combine parallel resistors
    edges_to_check = list(G.edges(data=True))
    edge_dict = {}

    for u, v, data in edges_to_check:
        key = tuple(sorted((u, v)))
        if key not in edge_dict:
            edge_dict[key] = []
        edge_dict[key].append(data['resistance'])

    # Rebuild the graph with combined resistors
    H = nx.Graph()
    for (u, v), resistances in edge_dict.items():
        if len(resistances) == 1:
            R_eq = resistances[0]
        else:
            R_eq = combine_parallel_resistors(resistances)
        H.add_edge(u, v, resistance=R_eq)

    return H

# Example usage
G = nx.MultiGraph()
G.add_edge('A', 'B', resistance=2)
G.add_edge('A', 'B', resistance=3)
G.add_edge('B', 'C', resistance=4)

simplified = simplify_circuit(G)
for u, v, data in simplified.edges(data=True):
    print(f"Edge {u}-{v}: {data['resistance']} Ohms")
