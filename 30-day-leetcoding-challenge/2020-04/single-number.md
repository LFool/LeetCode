# Single Number

## Description

Given a **non-empty** array of integers, every element appears _twice_ except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

> **Input:** \[2,2,1\] 
>
> **Output:** 1

**Example 2:**

> **Input:** \[4,1,2,1,2\] 
>
> **Output:** 4

## **Code**

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int singleNumber(int[] nums) {
        HashMap<Integer, Integer> hm = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (hm.containsKey(nums[i])) {
                hm.put(nums[i], hm.get(nums[i]) + 1);
            } else {
                hm.put(nums[i], 1);
            }
        }
        List<Map.Entry<Integer, Integer>> list = new ArrayList(hm.entrySet());
        list.sort(Comparator.comparingInt(Map.Entry::getValue));
        return list.get(0).getKey();
        
    }
}
```
{% endtab %}

{% tab title="XOR" %}
```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int i = 0; i < nums.length; i++) {
            result ^= nums[i];
        }
        return result;
    }
}
```
{% endtab %}
{% endtabs %}



