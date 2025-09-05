# **Autonomous Delivery Agent (2D Grid)**

A Python-based autonomous delivery agent that navigates a 2D grid city with terrain costs, static obstacles, and dynamic moving obstacles. It includes BFS, UCS, and A\* pathfinding, as well as a hill-climbing-based replanning strategy.

## **Features**

* **Multiple Search Algorithms**: Includes Breadth-First Search (BFS), Uniform-Cost Search (UCS), and A\* with a Manhattan distance heuristic.  
* **Dynamic Obstacle Avoidance**: The agent can replan its path when moving obstacles block the way.  
* **Interactive GUI**: A visual grid shows real-time agent movement and path tracking.  
* **Terrain Costs**: Movement costs vary for different terrain types.  
* **Hill-Climbing Replanning**: Uses a local search strategy as a fallback if global replanning fails.  
* **Live Metrics**: Provides real-time tracking of path cost, number of replans, and conflicts.

## **Requirements**

* Python 3.9 or higher  
* No external dependencies (uses only the Python standard library)  
* Tkinter (typically included with Python)

## **Installation**

1. Clone or download this repository.  
2. Navigate to the project directory.  
3. No additional installation is required.

## **Usage**

### **GUI Mode (Recommended)**

Run the interactive GUI with the following command:

python gui.py

#### **GUI Controls**

* **Width/Height**: Set the grid dimensions.  
* **Seed**: Use a random seed for reproducible results.  
* **Algorithm**: Choose between BFS, UCS, or A\*.  
* **Speed**: Adjust the animation speed in milliseconds.  
* **Mode**: Set the Goal, Set the Start, or Toggle Walls.  
* **New World**: Generate a new random grid.  
* **Start/Pause/Step**: Control the simulation flow.  
* **Reset Agent**: Return the agent to its starting position.  
* **Show Path**: Toggle the path visualization on or off.

### **CLI Mode**

Run the command-line simulator with the following command, replacing the values as needed for each planner:

python simulate.py \--algo astar \--width 20 \--height 12 \--seed 7

#### **CLI Options**

* \--algo: The search algorithm to use (bfs, ucs, or astar).  
* \--width: The grid's width (default: 20).  
* \--height: The grid's height (default: 12).  
* \--seed: The random seed (default: 7).  
* \--steps: The maximum number of simulation steps (default: 400).  
* \--print-every: The frequency of printing updates (default: 1).

## **Project Structure**

aiml/  
├── delivery/  
│   ├── \_\_init\_\_.py  
│   ├── grid.py          \# Grid model with terrain costs and obstacles  
│   ├── dynamic.py       \# Dynamic obstacle models  
│   ├── search.py        \# BFS, UCS, A\* algorithms  
│   └── agent.py         \# Delivery agent with replanning  
├── gui.py               \# Interactive GUI  
├── simulate.py          \# CLI simulator  
├── experiments.py       \# Benchmarking script  
├── requirements.txt     \# Dependencies  
└── README.md            \# This file

## **How It Works**

### **Environment Model**

* **Grid**: A 2D grid where cells have integer terrain costs from 1 to 5\.  
* **Static Obstacles**: Impassable walls are represented by black cells.  
* **Dynamic Obstacles**: Moving red 'X' cells that follow predetermined patrol paths.  
* **Start/Goal**: The agent starts at (0,0) and aims for the goal at (width-1, height-1).

### **Search Algorithms**

* **BFS**: Breadth-First Search, which minimizes the number of steps taken.  
* **UCS**: Uniform-Cost Search, which minimizes the total path cost.  
* **A**\*: A\* Search, which uses a Manhattan distance heuristic to find the most efficient path.

### **Replanning Strategy**

* The agent continuously checks for conflicts with dynamic obstacles at each step.  
* If the agent's path is blocked, it performs a full replanning from its current position.  
* A hill-climbing local search is used as a fallback if the global replanning fails.

## **Examples**

### **Basic Usage**

Run the GUI with default settings:

python gui.py

### **CLI Examples**

Run A\* on a 30x20 grid with a seed of 42:

python simulate.py \--algo astar \--width 30 \--height 20 \--seed 42

Run BFS with a custom grid size and step count:

python simulate.py \--algo bfs \--width 15 \--height 10 \--steps 200 \--print-every 5

## **Grid Legend**

* **S**: Start position (green border)  
* **G**: Goal position (blue)  
* **A**: Agent (yellow circle with time)  
* **\#**: Static wall (black)  
* **X**: Dynamic obstacle (red)  
* **Numbers**: Terrain cost (1-5, with lighter colors indicating cheaper costs)  
* **Purple line**: The agent's planned path

## **Troubleshooting**

### **Common Issues**

**GUI doesn't open**:

* Ensure you have a desktop environment.  
* Check if Tkinter is installed by running python \-c "import tkinter".

**Agent gets stuck**:

* Try a different random seed or a different algorithm.  
* Increase the maximum number of steps using the \--steps option.

## **Contributing**

1. Fork the repository.  
2. Create a feature branch.  
3. Make your changes.  
4. Test your changes thoroughly.  
5. Submit a pull request.

## **License**

This project is open source and available under the MIT License.

For more details, please refer to the source code or run python experiments.py for performance benchmarks.