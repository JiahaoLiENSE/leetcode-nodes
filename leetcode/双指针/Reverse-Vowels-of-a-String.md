### 345. Reverse Vowels of a String

#### Description
`Write a function that takes a string as input and reverse only the vowels of a string.`  

#### Example
Input: `"hello"`  
Output: `"holle"`

Input: `"leetcode"`  
Output: `"leotcede"`  

#### Java

```java
class Solution {
    private final static HashSet<Character> vowels = new HashSet <>(
    Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));
        
    public String reverseVowels(String s) {
        if(s == null) return null;
        int i = 0;
        int j = s.length() - 1;
        char [] result = s.toCharArray();
        while(i <= j) {
            char ci = s.charAt(i);
            char cj = s.charAt(j);
            if(!vowels.contains(ci)) {
                result[i++] = ci;
            } else if(!vowels.contains(cj)) {
                result[j--] = cj;
            } else {
                result[i++] = cj;
                result[j--] = ci;
            }
        }
        return new String(result);
    }
}
```

#### Python

```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        if not s:
            return ''
        
        vowels = {'a', 'e', 'i', 'o', 'u' , 'A', 'E', 'I', 'O', 'U'}
        toList = list(s)
        
        i = 0
        j = len(s) - 1
        while i < j:
            if toList[i] in vowels and toList[j] in vowels:
                toList[i], toList[j] = toList[j], toList[i]
                i += 1
                j -= 1
            elif toList[i] not in vowels:
                i += 1
            elif toList[j] not in vowels:
                j -= 1
            else:
                i += 1
                j -= 1
        return ''.join(toList)
```
