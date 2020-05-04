# Backspace String Compare

## Description

Given two strings `S` and `T`, return if they are equal when both are typed into empty text editors. `#` means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

**Example 1:**

> Input: S = "ab\#c", T = "ad\#c" 
>
> Output: true 
>
> Explanation: Both S and T become "ac".

**Example 2:**

> Input: S = "ab\#\#", T = "c\#d\#" 
>
> Output: true 
>
> Explanation: Both S and T become "".

**Example 3:**

> Input: S = "a\#\#c", T = "\#a\#c" 
>
> Output: true 
>
> Explanation: Both S and T become "c".

**Example 4:**

> Input: S = "a\#c", T = "b" 
>
> Output: false 
>
> Explanation: S becomes "c" while T becomes "b".

**Note**:

* `1 <= S.length <= 200`
* `1 <= T.length <= 200`
* `S` and `T` only contain lowercase letters and `'#'` characters.

**Follow up:**

* Can you solve it in `O(N)` time and `O(1)` space?

## **Code**

```java
class Solution {
    public boolean backspaceCompare(String S, String T) {
        int indexS = S.indexOf('#');
        int indexT = T.indexOf('#');
        while (indexS != -1) {
            S = indexS == 0 ? S.substring(indexS + 1) : S.substring(0, indexS - 1) + S.substring(indexS + 1);
            indexS = S.indexOf('#');
        }
        while (indexT != -1) {
            T = indexT == 0 ? T.substring(indexT + 1) : T.substring(0, indexT - 1) + T.substring(indexT + 1);
            indexT = T.indexOf('#');
        }
        return S.equals(T);
    }
}
```

