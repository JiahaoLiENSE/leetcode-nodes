###
#### Description
#### Example
#### Java
```java
// Compare each chars between s and t to see if chars of t are matching or not by iterating from begin.

// Solution 1 (faster):
class Solution {
    public boolean isSubsequence(String s, String t) {
        if(s.length() == 0) {
            return true;
        }
        if(t.length() == 0) {
            return false;
        }
        
        int index = -1;
        for(char c : s.toCharArray()) {
            index = t.indexOf(c, index + 1);
            // last char of t
            if(index == -1) {
                return false;
            }
        }
        return true;
    }
}

// Solution 2 (greedy):
class Solution {
    public boolean isSubsequence(String s, String t) {
        int i = 0;
        int j = 0;
        for (; j < t.length(); j++) {
            if(i == s.length()) {
                return true;
            }
            if(s.charAt(i) == t.charAt(j)) {
                i++;
            }
        }
        return i == s.length();
    }
}
```
#### Python
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        if len(s) == 0:
            return True
        if len(t) == 0:
            return False
        
        j = 0
        for i in range(len(t)):
            if j >= len(s):
                break
            if s[j] == t[i]:
                j += 1
        return j == len(s)
  ```
