# Two Sum

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have _**exactly**_ one solution, and you may not use the _same_ element twice.

**Example:**

> Given nums = \[2, 7, 11, 15\], target = 9,
>
> Because nums\[0\] + nums\[1\] = 2 + 7 = 9, return \[0, 1\].

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> hm = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (hm.containsKey(target - nums[i])) {
                return new int[]{hm.get(target - nums[i]), i};
            }
            hm.put(nums[i], i);
        }
        return null;
    }
}
```



