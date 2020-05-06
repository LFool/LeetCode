# Majority Element

## Description

Given an array of size n, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

**Example 1:**

> **Input:** \[3,2,3\] 
>
> **Output:** 3

**Example 2:**

> **Input:** \[2,2,1,1,1,2,2\] 
>
> **Output:** 2

## code

```java
class Solution {
    public int majorityElement(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        int max = 0, res = 0;

        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
            max = Math.max(max, map.get(num));
            res = max  == map.get(num) ? num : res;
        }
        return res;
    }
}
```

