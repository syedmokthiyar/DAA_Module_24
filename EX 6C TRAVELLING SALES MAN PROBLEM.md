# EX 6C TRAVELLING SALES MAN PROBLEM
## DATE:
## AIM:
To Solve Travelling Sales man Problem for the following graph.

![image](https://github.com/user-attachments/assets/653921a4-3d7b-4691-9b41-735e80f7af0b)



## Algorithm
1. Represent the graph as a cost matrix dist[n][n], where dist[i][j] is the cost to go from city i to city j.

2. Create a DP table:
    dp[mask][i] = minimum cost to reach city i having visited cities in mask (a bitmask of visited cities).

3. Initialize:

   dp[1 << 0][0] = 0 — start from city 0 with only city 0 visited.

4. Fill DP table:

    For all bitmasks mask, for all cities i in mask, update:
   dp[mask][i] = min(dp[mask][i], dp[mask ^ (1 << i)][j] + dist[j][i])
   for all j in mask where j != i.

5. Get result:

   The final answer is:
   min(dp[all_visited_mask][j] + dist[j][0])
   for all j ≠ 0, where all_visited_mask = (1 << n) - 1
## Program:
Developed by: GANESH R

Register Number:  212222240029
```python
from sys import maxsize
from itertools import permutations
V = 4
 

def travellingSalesmanProblem(graph, s):
 
   ## Write your code
    vetex=[]
    cur=0
    minpath=maxsize
    for i in range(V):
        if i!=s:
            vetex.append(i)

    nextper=permutations(vetex)
    for i in nextper:
        cur=0
        k=s
        for j in i:
            cur+=graph[k][j]
            k=j
        cur+=graph[k][s]
        minpath=min(minpath,cur)
    return minpath
 
 

if __name__ == "__main__":
 
    graph = [[0, 10, 15, 20], [10, 0, 35, 25],
            [15, 35, 0, 30], [20, 25, 30, 0]]
    s = 0
    print(travellingSalesmanProblem(graph, s))

```

## Output:

![image](https://github.com/user-attachments/assets/648a5869-a297-4a85-9a64-e05df1c1d09e)


## Result:
Thus the program was executed successfully for finding the minimum cost to vist all cities.
