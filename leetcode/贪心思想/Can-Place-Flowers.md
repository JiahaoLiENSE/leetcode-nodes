### 605. Can Place Flowers
#### Description
```
You have a long flowerbed in which some of the plots are planted, and some are not. However, 
flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, 
return if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule.
```
#### Example
```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: true
```
```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: false
```
#### Java
```java
// assume current position equals to 0, check previous position of current position equals to 0, next position of current position equals to 0;
// if all three positions are 0, a flower can be planted, until n flowers equals to 0.
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int len = flowerbed.length;
        if(len == 0) {
            return false;
        }
        if(n == 0){
            return true;
        }
        
        int i = 0;
        while(i < len) {
            if(flowerbed[i] == 0) {
                int pre = i == 0 ? 0 : flowerbed[i-1];
                int next = i == len - 1 ? 0 : flowerbed[i+1];
                if(pre == 0 && next == 0) {
                    flowerbed[i] = 1;
                    n--;
                }
                if(n <= 0) {
                    return true;
                }
            }
            i++;    
        }
        return false;
    }
}
```
#### Python
```python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        length = len(flowerbed)
        if length == 0:
            return False
        
        for i in range(length):
            if flowerbed[i] == 0 and (i == 0 or flowerbed[i-1] == 0) and (i == length - 1 or flowerbed[i+1] == 0):
                flowerbed[i] = 1
                n -= 1
        if n <= 0:
            return True
            
```
