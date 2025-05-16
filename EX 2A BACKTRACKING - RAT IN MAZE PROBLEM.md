# EX:2A - BACKTRACKING - RAT IN A MAZE PROBLEM
## DATE:

## AIM:

To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm:

1. Initialize the maze and solution matrix
   - Create a 2D list to represent the maze (1 for path, 0 for blocked).
   - Initialize another 2D list of the same size with all zeros to store the solution path.
2. Start from the top-left corner (0, 0)
   - Begin the path from the first cell.
   - Check if the current cell is safe to move (within bounds and has a value of 1).
3. Explore possible moves (right and down)
   - Move to the next cell by going either:
   - Right (x, y+1) or
   - Down (x+1, y)
   - Recursively check each move for safety and whether it leads to the destination.
4. Backtrack if no path is found
   - If neither move leads to a solution, backtrack by setting the current cell in the solution matrix back to 0.
5. Print the solution path or show no solution exists
   - If the bottom-right corner is reached, print the solution matrix.
   - If all paths are blocked, display that no solution exists.

## Program:

```
Program to implement Rat in a Maze.
Developed by: NIRAUNJANA GAYATHRI G R
Register Number: 212222230096

```

```
N = 4
 
def printSolution( sol ):
     
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 

def isSafe( maze, x, y ):
     
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
     
    return False
 

def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     
def solveMazeUtil(maze, x, y, sol):
    if x==N-1 and y==N-1 and maze[x][y]==1:
        sol[x][y]=1
        return True
    if isSafe( maze, x, y ):
        sol[x][y]=1
        if solveMazeUtil(maze, x+1, y, sol):
            return True
        if solveMazeUtil(maze, x, y+1, sol):
            return True
        sol[x][y]=0
    return False

if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)
```

## Output:

![image](https://github.com/user-attachments/assets/51dbaf66-da24-40c0-80a2-bfc7f33159c6)


## Result:

The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
