# Bitwise AND of Numbers Range

Given a range \[m, n\] where 0 &lt;= m &lt;= n &lt;= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

**Example 1:**

> **Input:** \[5,7\] 
>
> **Output:** 4

**Example 2:**

> **Input:** \[0,1\] 
>
> **Output:** 0

```java
class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        int step = 0;
        while(m!=n){
            m >>= 1;
            n >>= 1;
            step ++;
        }
        return m<<step;
    }
}
```

