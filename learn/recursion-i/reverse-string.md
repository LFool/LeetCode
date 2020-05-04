# Reverse String

## Description

Write a function that reverses a string. The input string is given as an array of characters `char[]`.

Do not allocate extra space for another array, you must do this by **modifying the input array** [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) with O\(1\) extra memory.

You may assume all the characters consist of [printable ascii characters](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

**Example 1:**

> **Input:** \["h","e","l","l","o"\] 
>
> **Output:** \["o","l","l","e","h"\]

**Example 2:**

> **Input:** \["H","a","n","n","a","h"\] 
>
> **Output:** \["h","a","n","n","a","H"\]

## **Code**

{% tabs %}
{% tab title="Iteration" %}
```java
class Solution {
    public void reverseString(char[] s) {
        int left = 0;
        int right = s.length - 1;
        while (left < right) {
            char t = s[left];
            s[left] = s[right];
            s[right] = t;
            left++;
            right--;
        }
    }
}
```
{% endtab %}

{% tab title="Recursion" %}
```java
public String reverseString(String s) {
    int len = s.length();
    if (len <= 1) return s;
    String leftStr = s.substring(0, len / 2);
    String rightStr = s.substring(len / 2, len);
    return reverseString(rightStr) + reverseString(leftStr);
}
```
{% endtab %}
{% endtabs %}

