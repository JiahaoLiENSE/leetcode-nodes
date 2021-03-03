### 451. Sort Characters By Frequency

#### Description
`Given a string, sort it in decreasing order based on the frequency of characters.`  

#### Example
Input: `"tree"`  
Output: `"eert"`  
Explanation:  
`'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.`  

#### Java
```java
class Solution {
    public String frequencySort(String s) {
        if(s == null) {
            return null;
        }
        Map<Character, Integer> frequencyForChar = new HashMap<>();
        // getOrDefault(object key, defaultVal): used to get the value mapped with specified key. If no value is mapped with the provided key then the default value is returned.
        // Return Value: This method returns value mapped with the specified key, otherwise default value is returned.
        for(char c : s.toCharArray()) {
            frequencyForChar.put(c, frequencyForChar.getOrDefault(c, 0) + 1);
        }
        
        // Group and sort most frequent element into arraylist.
        // HashMap -> keySet() method: 
        //    Definition: used to create a set out of the key elements contained in the hash map.
        //    Parameters: The method does not take any parameter.
        //    Return Value: The method returns a set having the keys of the hash map.
        //    More on: https://www.geeksforgeeks.org/hashmap-keyset-method-in-java/
        List<Character>[] buckets = new ArrayList[s.length() + 1];
        for(char key : frequencyForChar.keySet()) {
            int frequency = frequencyForChar.get(key);
            if(buckets[frequency] == null) {
                buckets[frequency] = new ArrayList<>();
            }
            buckets[frequency].add(key); 
        }
        
        // The StringBuilder in Java represents a mutable sequence of characters(可变的字符序列)
        // 将character, integer, string的ArrayList转变成String的一种方法。 更多：https://www.geeksforgeeks.org/stringbuilder-class-in-java-with-examples/
        StringBuilder builder = new StringBuilder();
        for(int i = buckets.length - 1; i >= 0; i--) {
            if(buckets[i] == null) {
                continue;
            }
            for(char key : buckets[i]) {
                for(int j = 0; j < i; j++) {
                    builder.append(key);
                }
            }
        }
        return builder.toString();
    }
}
```

#### Python
```python
class Solution:
    def frequencySort(self, s: str) -> str:
        frequency = {}
        for c in s:
            if c not in frequency:
                frequency[c] = 1
            else:
                frequency[c] += 1
                
        sortedList = sorted(frequency.items(),key = lambda k:k[1],reverse = True)
        
        result = ''
        for (k,v) in sortedList:
            result += k * v
        return result
```
