# EX 6B KNAPSACK PROBLEM
## DATE:
## AIM:
To demonstrate a python program using dynamic programming for 0/1 knapsack problem.



## Algorithm
1. Create a 2D DP table dp[n+1][W+1] to store the max value for each item and weight capacity.

2. Initialize the first row and column of the table with 0 (no items or no capacity).
   
3. If the item's weight ≤ current capacity:

     dp[i][w] = max(value with item, value without item)

5. Else:

    dp[i][w] = value without item

6. Return the value at dp[n][W] — the max value you can carry.

## Program:
Developed by: GANESH R

Register Number:  212222240029

```python
def knapSack(W, wt, val, n):
    dp=[[-1]*(W+1) for _ in range(len(val)+1)]
    for i in range(W+1):
        dp[0][i]=0
    for i in range(n+1):
        dp[i][0]=0
    for i in range(1,n+1):
        for j in range(1,W+1):
            if j<wt[i-1]:
                dp[i][j]=dp[i-1][j]
            else:
                dp[i][j]=max(dp[i-1][j],dp[i-1][j-wt[i-1]]+val[i-1])
    return dp[n][W]

x=int(input())
y=int(input())
W=int(input())
val=[]
wt=[]
for i in range(x):
    val.append(int(input()))
for y in range(y):
    wt.append(int(input()))

n = len(val)
print('The maximum value that can be put in a knapsack of capacity W is: ',knapSack(W, wt, val, n))

```

## Output:
![image](https://github.com/user-attachments/assets/0b346580-4b07-4cd4-b342-f3d17162b8b5)



## Result:
Thus the program was executed successfully for finding the maximum value that can be put in a knap sack of capacity .
