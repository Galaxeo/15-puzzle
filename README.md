# 15-puzzle
In collaboration with my friend [Seeger](https://github.com/seeger22).

## Description
The NxN-puzzle is a commonly discussed problem when it comes to artificial intelligence. In our case, we dealt with solving 4x4 puzzles, or 15-puzzle problems. These problems involved having a 4x4 grid with unique numbers in various positions, and a blank square that can swap positions with numbers by shifting up, down, left, or right. 

Our input files were given as such:  
1.0

1 5 3 13  
8 0 14 4  
15 10 7 2  
11 6 9 12  

1 5 3 13  
8 10 14 4  
0 15 9 2  
11 7 6 12

The first number is the weight for a weighted A* search, the first 4x4 grid of numbers is the initial state, and the second grid is the goal state. 0 represents the blank square that we use to swap the numbers around.


## Solution and Implementation
In order to solve this problem and put the numbers in their desired positions, we utilized A* search with the Manhattan distances of each number as our heuristic. The input file would first be read to get the weight (for acceptable answers) and then the 4x4 grids would be turned into a two 2-d matrices in the form of lists of lists. The goal state and initial state lists would then be inputted into a Puzzle class. The class internally keeps track of the path cost, depth, f-values of the path, and the actions needed to reach the specific state. This made it so that once we found a goal node, it was simple to access that node's data and what we needed for our output. It also contains functions to return the position of any number, swap the positions of numbers, get the Manhattan distances of each number, and generate the child nodes of the possible moves from the current state.

The frontier for the A* search has all of the nodes in the form of the Puzzle class previously described. At first, it only has the initial state, but once that state is expanded, each of the possible states from the available moves are added to the frontier. The minimum f-value is then used as our next node, and this process continues until we find a goal node to print.

We utilized argparse to read the input file and set an output file, so a sample input in terminal would be: `python run.py --infile Input1.txt --outfile Output1.txt`

Once an answer is found within the satisfactory weighing, we print out the depth of the search, the nodes generated, actions taken by the blank space, and the f-values of the A* search at each part of the solution path. 

Example below:

1  5 3 13  
8  0 14 4  
15 10 7 2  
11 6 9 12  

1 5 3 13  
8 10 14 4  
0 15 9 2  
11 7 6 12  

1.0  
6  
19  
D R D L U L   
6.0 6.0 6.0 6.0 6.0 6.0 