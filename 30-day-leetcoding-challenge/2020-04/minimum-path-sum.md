# Minimum Path Sum

## Description

Given a _m_ x _n_ grid filled with non-negative numbers, find a path from top left to bottom right which _minimizes_ the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

**Example:**

```text
Input:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
Output: 7
Explanation: Because the path 1→3→1→1→1 minimizes the sum.
```

## **Code**

```java
class Solution {
    
    public int minPathSum(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;

        int[] cur = new int[m];
        cur[0] = grid[0][0];

        for (int i = 1; i < m; i++) {
            cur[i] = cur[i - 1] + grid[i][0];
        }

        for (int i = 1; i < n; i++) {
            cur[0] += grid[0][i];
            for (int j = 1; j < m; j++) {
                cur[j] = grid[j][i] + Math.min(cur[j - 1], cur[j]);
            }
        }
        return cur[m - 1];
    }

}
```

