# A* Algorithm Visualizer

## About the A* search Algorithm

A* (pronounced "A-star") is a powerful and efficient algorithm used for finding the shortest path between two points in a map or network represented as a graph. It's widely employed in various applications, including:

- **Robotics:** Guiding robots to navigate their environment efficiently.
- **Video games:** Creating realistic pathfinding for in-game characters.
- **GPS navigation systems:** Determining the optimal route for drivers.

### Key Concepts:

- **Graphs:** A* operates on graphs, where nodes (vertices) represent locations, and edges (connections) represent paths between those locations. Each edge has a weight associated with it, signifying the cost of traversing that path (e.g., distance, time, fuel consumption).
- **Heuristic Function (h(n)):** A crucial component of A*, the heuristic function estimates the cost of reaching the goal node from any given node (n) in the exploration process. It's essentially an informed guess that guides the algorithm towards the most promising paths. The effectiveness of A* heavily relies on having a good heuristic function that is both admissible (never overestimates the actual cost) and informative (provides a reasonably accurate estimate).

### How A* Works:

- **Initialization:** The algorithm starts at the source node (the starting point) and marks it as "visited." It creates two sets:

  - Open Set: This set holds nodes that are yet to be explored but are considered promising candidates for the next step. It's typically implemented as a priority queue, where nodes are prioritized based on a scoring function (f(n)).
  - Closed Set: This set stores nodes that have already been explored and won't be revisited.
- **Iteration:** The algorithm iterates until the goal node is found:

  - If the open set is empty, there's no path to the goal (in rare cases, if the heuristic is flawed).
  - The node with the lowest f(n) score is removed from the open set and marked as "current."
  - For each neighbor (adjacent node) of the current node:
    - If the neighbor is in the closed set, skip it (already explored).
    - Calculate the tentative cost (g(n)) of reaching the neighbor from the source node through the current node. This is the sum of the cost to reach the current node (g(current)) and the cost of the edge connecting the current node to the neighbor.
    - If the neighbor is not in the open set or the tentative cost is lower than the previously recorded cost for the neighbor, update the neighbor's g(n) score and set its parent node to the current node. This establishes the path leading to the neighbor.
    - Calculate the neighbor's f(n) score, which is the sum of its g(n) score and the heuristic estimate (h(n)) of the cost to reach the goal from the neighbor.
    - Add the neighbor (if not already present) to the open set with its f(n) score for prioritization.
- **Goal Reached:** If the current node is the goal node, the algorithm has successfully found the shortest path. It can backtrack through the parent pointers to reconstruct the complete path from the source to the goal.

### The Power of A*:

- **Optimality:** When the heuristic function is admissible, A* guarantees finding the shortest path between the source and goal nodes.
- **Efficiency:** By prioritizing nodes based on their f(n) scores, A* focuses on exploring the most promising paths first, leading to significant efficiency gains compared to algorithms that blindly explore all possibilities.

### Evaluating the A* algorithm

- **Time Complexity:**

  - **Worst-case:** O(b^d), where:
  
    - b is the branching factor (average number of neighbors per node in the graph).
    - d is the depth of the solution (shortest path length).
      
    **Justification:** In the worst-case scenario, the heuristic function might be poor, leading A* to explore a significant portion of the search space. This exploration can grow exponentially with the branching factor and depth, resulting in the O(b^d) complexity.
  
  - **Best-case:** O(1), when the goal node is the immediate neighbor of the source node.
  
  - **Average-case:** Difficult to determine analytically, as it heavily depends on the specific problem and the quality of the heuristic function.

- **Space Complexity:**

    O(b^d), because A* needs to store information (f(n) score, parent pointer) for all nodes in the open set, and in the worst case, all nodes might be explored, leading to space usage proportional to the size of the search space (b^d).

- **Factors Affecting Complexity:**

  - **Quality of Heuristic Function:** A good heuristic that closely estimates the actual cost to the goal can significantly reduce the number of nodes explored, leading to better time and space complexity.
  - **Graph Structure:** Sparse graphs with a low branching factor (few neighbors per node) will generally have lower complexity compared to dense graphs with many connections.

### Considerations:

- The quality of the heuristic function significantly impacts A*'s performance. A good heuristic can dramatically reduce the number of nodes explored and speed up pathfinding.
- A* can be computationally expensive for very large graphs, as it maintains sets of nodes and needs to calculate f(n) scores for many nodes.

## How to run the visualizer

- This code uses the **Pygame** module to create the GUI which runs the visualization process.
- In order to run the code successfully, the Pygame module should be installed on the local systems.
- To install the Pygame module, type the code `python -m pip install pygame` in the Command Prompt and wait for it to finish the installation process.
- After installation of Pygame, the code can be run by executing the `main.py` file in the repository.

## Instructions to visualize the algorithm

- In the grid that is displayed, click on any box to mark it as the starting square (Colour coded with `ORANGE`)
- After the starting square is marked, click on any other square to mark it as the goal node or the target square (Colour coded with `TURQUOISE`)
- Once the start and the target squares are marked, click and drag the mouse pointer over the squares that you choose to make the obstacles or barriers (The barriers are colour coded with `BLACK`)
- Once all necessary squares are marked, press the `SPACEBAR` to start the visualization
- The open sets are represented by `GREEN` while the closed sets are represented by `RED`
- The shortest path from the start node to the target node is highlighted by `PURPLE`

## Issue handling

To report any bug with the code, feel free to pull an issue regarding the same
