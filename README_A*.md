# Algorithms

# A* Pathfinding Visualizer with Perlin Noise

An interactive Python implementation of the **A* (A-Star) Search Algorithm** designed to run in Google Colab. This project visualizes how the algorithm explores a grid-based environment to find the shortest path while navigating around procedurally generated obstacles.

##  Overview
The visualizer creates a grid where obstacles are generated using **Perlin Noise**, creating organic, cave-like structures. The algorithm uses a **Manhattan Distance heuristic** to efficiently navigate from the top-left start point to the bottom-right destination.

### Key Features:
* **A* Algorithm**: Implemented with real-time cost calculation.
* **Procedural Generation**: Custom Perlin Noise class for realistic obstacle placement.
* **Dynamic Animation**: Built with `matplotlib.animation` to show the expansion of the "Open" and "Closed" sets.
* **Safety Zones**: Guaranteed 3x3 clearing at start/end points to prevent unsolvable maps.

---

##  Mathematical Background

The A* algorithm is an informed search algorithm that finds the shortest path by minimizing the total cost function $f(n)$.

### The Cost Function
For any given node $n$, the total estimated cost is defined as:
$$f(n) = g(n) + h(n)$$

Where:
* **$g(n)$ (Path Cost)**: The actual cost of the path from the start node to the current node $n$. In this grid implementation, each step has a cost of 1.
* **$h(n)$ (Heuristic)**: The estimated "distance" from node $n$ to the goal. This is the "educated guess" that allows A* to outperform algorithms like Dijkstra.

### The Heuristic $h(n)$
To decide which direction to explore, this project uses the **Manhattan Distance**. It calculates the sum of the absolute differences of their coordinates:
$$h(n) = |x_{goal} - x_{n}| + |y_{goal} - y_{n}|$$



By combining $g(n)$ (where we have been) and $h(n)$ (how far we think we have left), the algorithm effectively balances exploration and efficiency.

---

##  Visual Legend
| Color | Meaning |
| :--- | :--- |
| **Black** | Empty Space (Walkable) |
| **Grey** | Wall/Obstacle (Blocked) |
| **Red** | **Closed Set**: Areas already explored by the algorithm |
| **Green** | **Open Set**: The current frontier being evaluated |
| **Blue** | **Path**: The calculated shortest route |
| **White/Yellow** | Start and End points respectively |

---

##  Installation & Usage

### Running in Google Colab
1. Copy the Python code provided in this repository.
2. Create a new notebook in [Google Colab](https://colab.research.google.com/).
3. Paste the code into a cell and run it.
4. The output will be an interactive HTML5 video player showing the search process.

### Configuration
You can modify the following variables at the top of the script to change the simulation:
```python
GRID_SIZE = 80          # Size of the square grid
NOISE_THRESHOLD = 0.32  # Increase for more walls (0.0 to 1.0)
NOISE_SCALE = 15.0      # Zoom level for the noise clusters
