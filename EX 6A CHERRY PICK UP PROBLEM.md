# EX 6A CHERRY PICK UP PROBLEM
## DATE:
## AIM:
To Create a python program for the following problem statement.
You are given an n x n grid representing a field of cherries, each cell is one of three possible integers.
0	means the cell is empty, so you can pass through,
1	means the cell contains a cherry that you can pick up and pass through, or
-1 means the cell contains a thorn that blocks your way.
Return the maximum number of cherries you can collect by following the rules below:
Starting at the position (0, 0) and reaching (n - 1, n - 1) by moving right or down through valid path cells (cells with value 0 or 1).
After reaching (n - 1, n - 1), returning to (0, 0) by moving left or up through valid path cells.
When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell 0. If there is no valid path between (0, 0) and (n - 1, n - 1), then no cherries can be collected.



## Algorithm
1. Start at (0, 0), move to (n-1, n-1) (only right or down)

2. Then return back to (0, 0) (only left or up)

3. Can pass through cells with 0 or 1

4. Can pick cherries (1) only once (cell becomes 0 after pick)

5. Avoid thorns (-1)

## Program:

Developed by: GANESH R

Register Number:  212222240029
```python
class Solution:
    def cherryPickup(self, grid):
        n = len(grid) 
        ### ADD
        dp = [[[-1] * n for _ in range(n)] for _ in range(n)]
        
        def f(x1, y1, x2):
            y2 = x1 + y1 - x2
            if x1 < 0 or y1 < 0 or x2 < 0 or y2 < 0 or grid[x1][y1] == -1 or grid[x2][y2] == -1:
                return float('-inf')
            if x1 == 0 and y1 == 0 and x2 == 0 and y2 == 0:
                return grid[0][0]
            if dp[x1][y1][x2] != -1:
                return dp[x1][y1][x2]
            cherries = grid[x1][y1]
            if x1 != x2 or y1 != y2:
                cherries += grid[x2][y2]
            cherries += max(
                f(x1 - 1, y1, x2 - 1),
                f(x1, y1 - 1, x2 - 1),
                f(x1 - 1, y1, x2),
                f(x1, y1 - 1, x2))
            
            dp[x1][y1][x2] = cherries
            return cherries


        result = max(0, f(n - 1, n - 1, n - 1))
        return result
obj=Solution()
grid=[[0,1,-1],[1,0,-1],[1,1,1]]        
print(obj.cherryPickup(grid))

```

## Output:
![image](https://github.com/user-attachments/assets/c2d18537-f033-4c29-b80e-f834d7a02142)



## Result:
Thus the above program was executed successfully for finding the maximum number of cherries from grid.
