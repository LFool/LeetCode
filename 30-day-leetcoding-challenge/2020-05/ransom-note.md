# Ransom Note

## Description

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**Note:**  
You may assume that both strings contain only lowercase letters.

> canConstruct\("a", "b"\) -&gt; false 
>
> canConstruct\("aa", "ab"\) -&gt; false 
>
> canConstruct\("aa", "aab"\) -&gt; true

## code:

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        Map<Character, Integer> map = new HashMap<>();
        char[] m = magazine.toCharArray();
        for (char c : m) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        char[] r = ransomNote.toCharArray();
        for (char c : r) {
            if (!map.containsKey(c) || map.get(c) == 0) {
                return false;
            }
            map.put(c, map.get(c) - 1);
        }
        return true;
    }
}
```

