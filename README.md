# Enchanted-Forest-Treasure-Hunt---Python-Implementation-using-Search-Algorithms-
This Python script implements a treasure hunt program set in an enchanted forest by traversing through optimal path. The program simulates traversing through a mystical forest grid to find hidden treasures. The optimal path is calculated in basis of Uniform Cost Search and A* Search algorithms.

Python Code Implementation for Pathfinding Algorithm
1. Grid Creation:

User inputs the grid size (rows and columns).
A 1D list of size rows * cols is created, initially filled with spaces (" ").
The makegrid() function populates the grid with characters like animals, walls, and obstacles using the addAttributes() function.
makegrid() randomly assigns a number of each character based on a list containing the maximum number of rows and other values below it.
The 1D grid is transformed into a 2D grid for easier manipulation.
The starting point ('S') and ending point ('T') are hardcoded into the 2D grid.
2. Cost and Heuristic Functions:

The cost_returner() function returns the cost based on user input:
If the user enters 't' or 'T', it uses pre-determined costs for accurate algorithm comparison.
Otherwise, it uses random values based on the current cell's state (space, animal, obstacle, or wall).
The heuristic_returner() function (optional for A* search) calculates heuristic values based on a provided formula.
3. Building the Adjacency List:

The add_edges() function creates an adjacency list representation of the grid:
It takes the current cell and its possible neighbors (up, down, left, right) as input.
It iterates through all cells in the grid and adds edges between neighboring cells.
The edges dictionary stores individual cells as keys and their neighbor lists (including costs) as values.
For A* search, the heuristic is added to the cost (later subtracted to avoid affecting actual cost, used only for comparison).

4. Sorting and Displaying Information:

The sort_queue() function sorts the queue based on the cost associated with each path. Since the costs are negative, so the one close to 0 is considered smaller.
The showPosition() function takes a node as input and displays the current location of the agent/hero ("o_o") on the grid.

5. Uniform Cost Search (UCS) Algorithm:

The ucs() function implements the UCS algorithm:
It takes the starting and goal coordinates as input.
It starts with the starting node in a queue.
The algorithm loops until the queue is empty or the goal is reached.
In each iteration, it:
	*Pops the first element (path and its cost) from the queue.
	*Removes the heuristic value from the cost (as it was added for comparison) iff the algorithm chosen is A*.
	*Iterates through the neighbors of the last node in the path.
	*Avoids redundancy by checking if node and neighbour was not visited before.
	*Adds unvisited neighbors to the queue with their costs (including heuristic in case of A*).
	*Sorts the updated queue based on their costs. 
	
Handles encountering walls:
If a wall is encountered at the beginning (neighbour of Starting node), move back one step by appending in queue the path without last node, i.e. path[:-1].
If a wall is encountered during traversal, move back two steps,  move back one step by appending in queue the path without last 2 nodes, i.e. path[:-2].
A cost of -1 (+ heuristic of node at end of path in case of A*) is added to cost.
The queue is sorted after each update based on the cost associated with each path.
6. Visualizing the Path:

The provided implementation showcases the path using asterisks (*) and animals represented by 'A'.


