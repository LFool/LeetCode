# Maximum Subarray

## Description

Given an integer array `nums`, find the contiguous subarray \(containing at least one number\) which has the largest sum and return its sum.

**Example:**

> **Input:** \[-2,1,-3,4,-1,2,1,-5,4\], 
>
> **Output:** 6 
>
> **Explanation:** \[4,-1,2,1\] has the largest sum = 6.

**Follow up:**

If you have figured out the O\(_n_\) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## **Code**

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = nums[0];
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            if (sum < 0) sum = 0;
            sum += nums[i];
            max = Math.max(sum, max);
        }
        return max;
        
    }
}
```
{% endtab %}

{% tab title="DP" %}
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        int max = nums[0];
        for (int i = 1; i < nums.length; i++) {
            dp[i] = dp[i - 1] > 0 ? dp[i - 1] + nums[i] : nums[i];
            max = Math.max(max, dp[i]);
        }
        return max;
    }
}
```
{% endtab %}
{% endtabs %}

