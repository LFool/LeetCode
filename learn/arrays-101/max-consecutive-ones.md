# Max Consecutive Ones

## Description

Given a binary array, find the maximum number of consecutive 1s in this array.

 **Example 1:**

> **Input:** \[1, 1, 0, 1, 1, 1, 1\]
>
> **Output:** 3
>
> **Explanation:** The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.

## **Code**

```java
public int findMaxConsecutiveOnes(int[] nums) {
    int result = 0;
    int count = 0;
    for (int num : nums) {
        if (num == 1) {
            count++;
        } else {
            result = Math.max(count, result);
            count = 0;
        }
    }
    return Math.max(count, result);
}
```







