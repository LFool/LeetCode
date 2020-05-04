# Valid Mountain Array

## Description

Given an array `A` of integers, return `true` if and only if it is a _valid mountain array_.

Recall that A is a mountain array if and only if:

* `A.length >= 3`
* There exists some `i` with `0 < i < A.length - 1` such that:
  * `A[0] < A[1] < ... A[i-1] < A[i]`
  * `A[i] > A[i+1] > ... > A[A.length - 1]`

![](https://assets.leetcode.com/uploads/2019/10/20/hint_valid_mountain_array.png)

**Example 1:**

> **Input:** \[2,1\] 
>
> **Output:** false

**Example 2:**

> **Input:** \[3,5,5\] 
>
> **Output:** false

**Example 3:**

> **Input:** \[0,3,2,1\] 
>
> **Output:** true

**Note:**

1. `0 <= A.length <= 10000`
2. `0 <= A[i] <= 10000` 

## **Code**

```java
public boolean validMountainArray(int[] A) {
    // 数组长度小于3返回false
    if (A.length < 3) {
        return false;
    }
    // flag代表该阶段是上升(0)还是下降(1)
    int flag = A[1] - A[0] > 0 ? 0 : 1;
    // 初始不上升则返回false
    if (flag != 0) {
        return false;
    }
    for (int i = 1; i < A.length; i++) {
        int t = A[i] - A[i - 1];
        // 两个值相等返回false
        if (t == 0) {
            return false;
        }
        // 首次出现下降时将flag的值置为1
        if (flag == 0 && t < 0) {
            flag = 1;
        }
        // 出现先升后降再升的情况返回false
        if (t > 0 && flag == 1) {
            return false;
        }
    }

    // 若flag最后不等于1，说明没有下降过
    return flag == 1;
}
```

