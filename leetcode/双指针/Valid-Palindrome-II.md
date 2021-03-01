### 680. Valid Palindrome II

#### Description
`Given a non-empty string s, you may delete at most one character. Judge whether you can make it a palindrome.`

### Example

Input: `"aba"`  
Output: `True`  

Input: `"abca"`  
Output: `True`  
`Explanation: You could delete the character 'c'.`

#### Java
```java
class Solution {
    public boolean validPalindrome(String s) {
        if(s == null) return false;
        int i = 0, j = s.length() - 1;
        while(i < j) {
            if(s.charAt(i) != s.charAt(j)) {
                return isPalindrome(s, i, j-1) || isPalindrome(s, i+1, j);
            }
            i++;
            j--;
        }
        return true;
    }
    
    private boolean isPalindrome(String s, int i, int j) {
        if(s == null) return false;
        while(i < j) {
            if(s.charAt(i) != s.charAt(j)) {
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
}
```

#### Python
```python
class Solution:
    def validPalindrome(self, s: str) -> bool:
        if not s:
            return False
        
        i = 0
        j = len(s) - 1
        lst = list(s)
        while i < j:
            if lst[i] != lst[j]:
                return isPalindrome(s, i, j-1) or isPalindrome(s, i+1, j)
            i += 1
            j -= 1
        return True
    
    def isPalindrome(self, s: str, i: int, j: int) -> bool:
        lst = list(s)
        while i < j:
            if lst[i] != lst[j]:
                return False
            i += 1
            j -= 1
        return True
```
