# Merge Sorted Array

Given two sorted integer arrays _nums1_ and _nums2_, merge _nums2_ into _nums1_ as one sorted array.

**Note:**

* The number of elements initialized in _nums1_ and _nums2_ are _m_ and _n_ respectively.
* You may assume that _nums1_ has enough space \(size that is greater or equal to _m_ + _n_\) to hold additional elements from _nums2_.

**Example:**

> **Input:** 
>
> nums1 = \[1,2,3,0,0,0\], m = 3 
>
> nums2 = \[2,5,6\],           n = 3
>
> **Output:** \[1,2,2,3,5,6\]

```java
// 从下标i开始将数组整体向后移动一格
public void moveFormI(int[] arr, int i) {
    if (arr.length - 1 - i >= 0) {
        System.arraycopy(arr, i, arr, i + 1, arr.length - 1 - i);
    }
}
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = 0, j = 0;
    int curLen = m;
    while (j < nums2.length) {
        if (i >= curLen) {
            nums1[i] = nums2[j];
            j++;
        } else if (nums2[j] <= nums1[i]) {
            moveFormI(nums1, i);
            nums1[i] = nums2[j];
            j++;
            curLen++;
        }
        i++;
    }
}
```

