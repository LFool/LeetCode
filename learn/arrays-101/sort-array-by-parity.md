# Sort Array By Parity



Given an array `A` of non-negative integers, return an array consisting of all the even elements of `A`, followed by all the odd elements of `A`.

You may return any answer array that satisfies this condition.

**Example 1:**

> **Input:** \[3,1,2,4\] 
>
> **Output:** \[2,4,3,1\] 
>
> The outputs \[4,2,3,1\], \[2,4,1,3\], and \[4,2,1,3\] would also be accepted.

**Note:**

* `1 <= A.length <= 5000`
* `0 <= A[i] <= 5000`

```java
public int[] sortArrayByParity(int[] A) {
    int i = 0;
    int j = A.length - 1;
    int t = 0;
    while (i < j) {
        while (A[i] % 2 != 1 && i < j) {
            i++;
        }
        while (A[j] % 2 != 0 && i < j) {
            j--;
        }
        t = A[i];
        A[i] = A[j];
        A[j] = t;
        i++;
        j--;
    }
    return A;
}
```
