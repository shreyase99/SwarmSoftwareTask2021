# Swarm Robotics Software Team Selections
## Pre-requisites
* Please install Ubuntu 18.04 or above on your laptop/WSL (Cannot verify the sanity of the codes for Windows machine)
* If you are on Windows 10 and you have Ubuntu 18.04 neither as Dual-Boot nor in WSL (Windows Subsystem for Linux), then you may install WSL from this [link](https://docs.microsoft.com/en-us/windows/wsl/install-win10)  
* Ensure you have Python3 and pip installed
* Ensure you have basic understanding of Python
* Please download/clone the latest version of this repository. If any bug is discovered, please communicate the deatils of the bug in Teams group. For the most updated codes, use `git pull swarm master`, once you have cloned the repository.

## Resources
* [Git and Github tutorial](https://in.udacity.com/course/how-to-use-git-and-github--ud775-india)
* [A* path planning algorithm](https://www.hackerearth.com/practice/notes/a-search-algorithm/)
* [Dijkstra path planning](https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/)
* [Obstacle Avoidance and Path Retracing](https://2019.robotix.in/tutorial/pathplanning/obstacleavoidance/)
* [RRT Path Planning](https://2019.robotix.in/tutorial/pathplanning/rrtplanner/)

## Submission Guidelines

You need to submit only `code.py` file over the Teams by deadline notified for the task.

There will be meetings held for doubts and help, on a per need basis.

## How to Run

This needs to be run either in a Ubuntu (>18.04) system or in WSL (Ubuntu 18.04) inside Windows.

Clone this repository (either download it, or use this command on a terminal: `git clone https://github.com/shreyase99/SwarmSoftwareTask2021`)

Please install the dependencies in `requirements.txt` (you can use `pip install -r requirements.txt`).

GRANTING PERMISSIONS:
Change the execution permissions of  setup.sh and run.sh by using the following commands:

  `chmod +x setup.sh`
  `chmod +x run.sh`

FIRST RUN:

In one terminal, enter the following:

  `./setup.sh`

The program would prompt you to enter a level. Start with 1 and work your way upto level 6.

In another terminal, run:

  `python controller.py`

If you want to view the simulations (not for WSL setup), run:

  `python simulation.py`

For those working on WSL, you can view the map by opening this link on browser:

  `http://localhost:5000/map`

Keep refreshing the page to see the changes in the map.


**Note for future runs:**  
Instead of running `setup.sh`, which may take some extra time confirming the dependencies, you may directly use:
	`./run.sh`
	
You need not stop/restart the `run.sh` process everytime, but only when the process had been stopped (Ctrl+C)

	*But make sure that you have all the dependencies installed before using this.*

Your task is to complete up as many functions/levels as possible in `code.py` and submit your codes through the teams assignment. You need not attempt all the levels, but sure, the more the better your chances are to get into the team. Your functions may not be optimal (in some cases, optimality cannot even be guaranteed!). We would solely judge on how you approach the problem and how much effort you've put in! :)

This problem statement comes with a sample (pretty unintelligent!) submission for level 1 problem. We shall be providing sample (again, unintelligent ones!) for higher levels too.

## Code Structure
There is really not much to play with. There is only one file named `code.py`, which you must edit and fill out the functions. You're encouraged to use solutions from the lower levels to solve problems of higher level. You can refer to the documentations in `api.py`, in case you are unsure about what a command does.

## Working Procedure
(PS: Please go through the problem description to understand the working procedure)

The file `app.py` is responsible for maintaining the grid, the position of the bots, handling multiple command requests and so on. The `controller.py` is responsible for simulating multiple bots, using threads. The `code.py` file uses functions from `api.py` to send commands to `app.py` which then replicates what would happen in the zooids' world. The `simulation.py` file, constantly fetches the current map and displays it. simulation.py would not work on WSL instances without a GUI server. In order to close it, please press Ctrl+C, on the terminal you run it.

To attempt a different level, just close the controller.py process and restart it with another level.

## Problem Description
The problem is based on the world of zooids, where you are their master. The world of zooid is a grid of dimension 200 x 200. As in any real world, there are obstacles occupying some portions of the grid. The obstacles are strictly rectangular in shape. Here is a sample image    
![sample image](images/curr_map.png)

Each zooid is capable of some basic locomotion. If the zooid is at a location X in a grid, then a movement of type 1, would take it to the grid marked as 1, a movement of type 2 would take it to the grid marked 2 and so on.

1 2 3

8 X 4

7 6 5

As such, zooids are pretty unintelligent beings. Your mission, should you choose to accept, is to make them intelligent and intelligent as a whole. You would learn what is an agent, what is an objective, what is environment, what is a more constrained environment, what is intelligence and how swarm intelligence works.

The obstacles (you cannot move through obstacles) are marked in the map in black, the moving blue colored objects are your zooids, the green colored regions are the ones you must visit, and the red colored regions are the ones you should avoid (you can go through them, but you will end up paying twice as much in any other traversable cell). At each level, the goal is to visit all the green colored regions in as minimum number of steps as possible.

### Level 1
The first level, is to make zooid Zoozoo aware of his capabilities, and show him that he can walk efficiently. Zoozoo's initial and final position will be known to you, and you have to guide Zoozoo through the grid to his destination. Once you reach the destination, you will be awarded a score. Your goal is to reach the destination with as little score as possible. This is an example of a single agent, single objective system.

### Level 2
The second level, is to make Zoozoo intelligent enough to go through all the green regions at least once. This is an example of a single agent, but multiple objective system.

### Level 3
They say, third's the charm! Zoozoo finally has a friend. They have many green regions to go through, and they should co-operate among themselves to achieve this goal with minimum steps. This is an example of multi-agent, multi-objective system.

### Level 4
Zoozoo and his friend have now wondered into a swarm. There are many more zooids, each equally capable as Zoozoo. And there are still more than one green regions to go through. Can they cooperate as a group? This should teach them something about swarm systems!

### Level 5
Zoozoo and his friend have now been landed into a harsher territory. It's only two of them and they are still to go through the green regions, but now, there are patches of red regions that they should ideally avoid, because each step through the red region is counted as 2 steps. But then, sometimes, it might be necessary to go through the red regions in order to avoid a longer way through the green one. Hmmmm.. they need some intelligence!

### Level 6
Now a swarm of zooids has joined in to help Zoozoo and his friend. This is the beginning of swarm intelligence. Now, do you feel like a God who programmed his creations to intelligence?