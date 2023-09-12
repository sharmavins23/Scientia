Breadth-first search (BFS) is an [[Algorithms|algorithm]] for traversal of a [[Graph (Network)|graph]]. It has a worst-case time complexity of $O(|V| + |E|)$, and a worst-case space complexity of $O(|V|)$.

## Distance between $v_a$, $v_b$: $d_{ab}$

The algorithm can be applied as follows:

1. Create a queue $Q$.
2. Label the starting node $v_a$ as explored.
3. Place $v_0$ in $Q$.
4. While $Q$ is not empty, pop out $v_i$ from the top of $Q$.
5. If $v_i = v_b$, then stop computing.
6. For all adjacent edges $E$ from $v_i$ (such that $(v_i, v_j) \in E$), if $v_j$ is not labelled as explored, then label $v_j$ as explored and add $v_j$ to the queue.
7. Repeat step 4 until $Q$ is empty.
8. If computation has not stopped, $d_{ab}=\infty$.

## Distance For All Nodes

The algorithm to find the distance from a starting node $v_x$ to all nodes is as follows:

1. Find all neighbors of the starting node $v_x$. These all have a distance of $1$ to $v_x$ (for a simple unweighted undirected graph). Label them as $1$.
2. Find all unlabeled neighbors of the nodes labelled as $1$, and label them as $2$.
3. Repeat step 2, incrementing, so on and so forth.