# Valid Perfect Square

## Description

Given a positive integer num, write a function which returns True if num is a perfect square else False.

**Note:** **Do not** use any built-in library function such as `sqrt`.

**Example 1:**

> **Input:** 16 
>
> **Output:** true

**Example 2:**

> **Input:** 14 
>
> **Output:** false

## code

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        int lo = 1, hi = num;
        while (lo < hi) {
            int mid = lo - (lo - hi) / 2;
            long temp = (long) mid * mid;
            if (temp == num) return true;
            else if (temp < num) lo = mid + 1;
            else hi = mid - 1;
        }
        return lo * lo == num;
    }
}
```

