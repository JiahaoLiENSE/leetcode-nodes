### 524. Longest Word in Dictionary through Deleting

#### Description
`Given a string s and a string array dictionary, return the longest string in the dictionary that can be formed by deleting some of the given string characters. If there is more than one possible result, return the longest word with the smallest lexicographical order. If there is no possible result, return the empty string.`  

#### Example
Input: `s = "abpcplea", dictionary = ["ale","apple","monkey","plea"]`  
Output: `"apple"`  

Input: `s = "abpcplea", dictionary = ["a","b","c"]`  
Output: `"a"`  

#### Java
```java
class Solution {
    public String findLongestWord(String s, List<String> dictionary) {
        if(s == null) return null;
        String longestWord = "";
        for(String target : dictionary) {
            int i = longestWord.length();
            int j = target.length();
            if(i > j || i == j && longestWord.compareTo(target) > 0) {  // Directly comparing counts of word from longestWord and target
                continue;
            }
            if(isSubsequence(s, target)) {
                longestWord = target;
            }
        }
        return longestWord;
    }
    
    private boolean isSubsequence(String s, String target) {
        int i = 0, j = 0;
        while(i < s.length() && j < target.length()) {
            if(s.charAt(i) == target.charAt(j)) {
                j++;
            }
            i++;
        }
        return j == target.length();
    }
}
```

#### Python
```python
```
