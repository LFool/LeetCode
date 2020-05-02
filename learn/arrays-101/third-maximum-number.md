# Third Maximum Number

Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O\(n\).

**Example 1:**

> **Input:** \[3, 2, 1\]
>
> **Output:** 1
>
> **Explanation:** The third maximum is 1.

**Example 2:**

> **Input:** \[1, 2\]
>
> **Output:** 2
>
> **Explanation:** The third maximum does not exist, so the maximum \(2\) is returned instead.

**Example 3:**

> **Input:** \[2, 2, 3, 1\]
>
> **Output:** 1
>
> **Explanation:** Note that the third maximum here means the third maximum distinct number. Both numbers with value 2 are both considered as second maximum.

{% tabs %}
{% tab title="Java" %}
```java
public int thirdMax(int[] nums) {
    final long minNum = Long.MIN_VALUE;
    long firstMax = minNum;
    long secondMax = minNum;
    long thirdMax = minNum;
    for (int num : nums) {
        firstMax = Math.max(firstMax, num);
    }
    for (int num : nums) {
        if (num != firstMax) {
            secondMax = Math.max(secondMax, num);
        }
    }
    for (int num : nums) {
        if (num != firstMax && num != secondMax) {
            thirdMax = Math.max(thirdMax, num);
        }
    }
    return (int) (thirdMax == minNum ? firstMax : thirdMax);
}
```
{% endtab %}

{% tab title="Java" %}
```java
public int thirdMax(int[] nums) {
    Integer firstMax = null;
    Integer secondMax = null;
    Integer thirdMax = null;

    for (Integer num : nums) {
        if (num.equals(firstMax) || num.equals(secondMax) || num.equals(thirdMax)) {
            continue;
        }
        if (firstMax == null || num > firstMax) {
            thirdMax = secondMax;
            secondMax = firstMax;
            firstMax = num;
        } else if (secondMax == null || num > secondMax) {
            thirdMax = secondMax;
            secondMax = num;
        } else if (thirdMax == null || num > thirdMax) {
            thirdMax = num;
        }
    }
    return thirdMax == null ? firstMax : thirdMax;
}
```
{% endtab %}
{% endtabs %}

