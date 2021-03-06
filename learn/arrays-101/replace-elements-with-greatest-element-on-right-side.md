# Replace Elements with Greatest Element on Right Side

## Description

Given an array `arr`, replace every element in that array with the greatest element among the elements to its right, and replace the last element with `-1`.

After doing so, return the array.

**Example 1:**

> **Input:** arr = \[17,18,5,4,6,1\] 
>
> **Output:** \[18,6,6,6,1,-1\]

**Constraints:**

* `1 <= arr.length <= 10^4`
* `1 <= arr[i] <= 10^5`

## **Code**

```java
// 从后向前求，向前移动一个单位时，只需要判断新增的数和原来最大值的大小
public int[] replaceElements(int[] arr) {
    int maxNum = arr[arr.length - 1];
    int t = arr[arr.length - 1];
    arr[arr.length - 1] = -1;
    for (int i = arr.length - 2; i >= 0; i--) {
        maxNum = Math.max(maxNum, t);
        t = arr[i];
        arr[i] = maxNum;
    }
    return arr;
}
```

