# Jewels and Stones

You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

**Example 1:**

> **Input:** J = "aA", S = "aAAbbbb" 
>
> **Output:** 3

**Example 2:**

> **Input:** J = "z", S = "ZZ" 
>
> **Output:** 0

**Note:**

* `S` and `J` will consist of letters and have length at most 50.
* The characters in `J` are distinct.

```java
class Solution {
    public int numJewelsInStones(String J, String S) {
        Map<Character, Integer> map = new HashMap<>();
        char[] s = S.toCharArray();
        for (int i = 0; i < s.length; i++) {
            map.put(s[i], map.getOrDefault(s[i], 0) + 1);
        }
        int count = 0;
        char[] j = J.toCharArray();
        for (int i = 0; i < j.length; i++) {
            if (map.containsKey(j[i])) {
                count += map.get(j[i]);
            }
        }
        return count;
    }
}
```

