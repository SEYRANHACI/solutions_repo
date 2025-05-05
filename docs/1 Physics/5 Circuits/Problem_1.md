# Problem 1



ir
ccuits  
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

    1.2

    Create a Python program that:

Accepts any circuit as a graph (nodes = junctions, edges = resistors),

Handles series, parallel, and nested combinations,

Calculates total equivalent resistance between two given nodes.

We'll use NetworkX to manage graph structure.

🔧 Approach
📌 1. Definitions
Series: Node with degree 2, not a start/end node → combine resistors.

Parallel: Multiple edges between same two nodes → combine resistors in parallel.

Repeat these reductions until only two nodes remain: the source and target.

import networkx as nx

def combine_parallel(resistances):
    inverse = sum(1/r for r in resistances)
    return 1 / inverse if inverse != 0 else float('inf')

def simplify_parallel(G):
    """Simplify all parallel edges between the same pair of nodes."""
    new_G = nx.Graph()
    edge_map = {}

    for u, v, data in G.edges(data=True):
        key = tuple(sorted((u, v)))
        edge_map.setdefault(key, []).append(data['resistance'])

    for (u, v), res_list in edge_map.items():
        if len(res_list) == 1:
            R_eq = res_list[0]
        else:
            R_eq = combine_parallel(res_list)
        new_G.add_edge(u, v, resistance=R_eq)

    return new_G

def simplify_series(G, source, target):
    """Collapse series nodes (degree 2 and not source/target)."""
    changed = True
    while changed:
        changed = False
        for node in list(G.nodes):
            if node in (source, target):
                continue
            neighbors = list(G.neighbors(node))
            if len(neighbors) == 2:
                u, v = neighbors
                R1 = G[node][u]['resistance']
                R2 = G[node][v]['resistance']
                R_new = R1 + R2
                G.remove_node(node)
                G.add_edge(u, v, resistance=R_new)
                changed = True
                break
    return G

def calculate_equivalent_resistance(G, source, target):
    G = simplify_parallel(G)
    G = simplify_series(G, source, target)
    if G.has_edge(source, target):
        return G[source][target]['resistance']
    else:
        return float('inf')  # disconnected

# ---------------------
# 🔬 EXAMPLES
# ---------------------

# Example 1: Simple Series
G1 = nx.MultiGraph()
G1.add_edge('A', 'B', resistance=2)
G1.add_edge('B', 'C', resistance=3)
G1 = simplify_parallel(G1)
R1 = calculate_equivalent_resistance(G1, 'A', 'C')
print("Example 1 (Series): R_eq =", R1)

# Example 2: Simple Parallel
G2 = nx.MultiGraph()
G2.add_edge('A', 'B', resistance=2)
G2.add_edge('A', 'B', resistance=4)
G2 = simplify_parallel(G2)
R2 = calculate_equivalent_resistance(G2, 'A', 'B')
print("Example 2 (Parallel): R_eq =", R2)

# Example 3: Nested Combination
G3 = nx.MultiGraph()
G3.add_edge('A', 'B', resistance=1)
G3.add_edge('B', 'C', resistance=1)
G3.add_edge('C', 'D', resistance=1)
G3.add_edge('A', 'D', resistance=2)  # Parallel to path A-B-C-D
G3 = simplify_parallel(G3)
R3 = calculate_equivalent_resistance(G3, 'A', 'D')
print("Example 3 (Nested): R_eq =", R3)

