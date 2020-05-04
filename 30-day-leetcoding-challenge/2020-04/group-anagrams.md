# Group Anagrams

## Description

Given an array of strings, group anagrams together.

**Example:**

> **Input:** \["eat", "tea", "tan", "ate", "nat", "bat"\], 
>
> **Output:** 
>
> \[ 
>
>     ****\["ate","eat","tea"\], 
>
>     \["nat","tan"\], 
>
>     \["bat"\]
>
>  \]

**Note:**

* All inputs will be in lowercase.
* The order of your output does not matter.

## **Code**

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs == null || strs.length == 0) return new ArrayList<>();
        Map<String, ArrayList<String>> map = new HashMap<>();
        for (String s : strs) {
            char[] ca = new char[26];
            for (char c : s.toCharArray()) ca[c - 'a']++;
            String keyStr = String.valueOf(ca);
            if (!map.containsKey(keyStr)) map.put(keyStr, new ArrayList<String>());
            map.get(keyStr).add(s);
        }
        return new ArrayList<>(map.values());
    }
}
```

