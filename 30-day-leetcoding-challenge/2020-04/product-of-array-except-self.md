# Product of Array Except Self

## Description

Given an array `nums` of _n_ integers where _n_ &gt; 1,  return an array `output` such that `output[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

**Example:**

> **Input:** \[1,2,3,4\] 
>
> **Output:** \[24,12,8,6\]

**Constraint:** It's guaranteed that the product of the elements of any prefix or suffix of the array \(including the whole array\) fits in a 32 bit integer.

**Note:** Please solve it **without division** and in O\(_n_\).

**Follow up:**  
Could you solve it with constant space complexity? \(The output array **does not** count as extra space for the purpose of space complexity analysis.\)

## **Code**

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int sum = 1;
        int zeroNum = 0;
        int[] output = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                sum *= nums[i];                
            } else {
                zeroNum++;
            }
        }
        if (zeroNum >= 2) return output;
        for (int i = 0; i < nums.length; i++) {
            if (zeroNum == 0) {
                output[i] = sum / nums[i];
            } else {
                if (nums[i] == 0) output[i] = sum;
                else output[i] = 0;
            }
        }
        return output;
    }
}
```

