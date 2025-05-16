# EX:2B - BACKTRACKING - NQUEEN PROBLEM
## DATE:

## AIM:

To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm

1. Input the size of the board (N)
   - Take input for the number of queens and the size of the NxN chessboard.
2. Place queens column by column using recursion
   - Start from the first column and try placing a queen in all rows one by one.
3. Check if placing the queen is safe
   - For each cell, check:
   --> The left row,
   --> The upper left diagonal,
   --> The lower left diagonal
   - Only proceed if all these are safe (i.e., no other queen is attacking).
4. Use backtracking to explore all possibilities
   - If placing the queen leads to a valid solution, move to the next column.
   - If not, backtrack by removing the queen and try the next row.
5. Print the board if all queens are placed
   - If queens are placed in all columns, print the board.
   - If not, print that no solution exists.

## Program:

```
Program to implement N-Queen problem using backtracking.
Developed by: NIRAUNJANA GAYATHRI G R
Register Number: 212222230096
```
```
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
      if col>=N:
          return True
      for i in range(N):
          if isSafe(board, i, col):
              board[i][col]=1
              if solveNQUtil(board, col+1):
                  return True
              board[i][col]=0
      return False

def solveNQ():
    board = [ [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0]]
 
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
```

## Output:

![image](https://github.com/user-attachments/assets/f513aad1-353b-4933-9b21-856de211463c)


## Result:

The N-Queens program executed successfully, and a valid board configuration was generated.
