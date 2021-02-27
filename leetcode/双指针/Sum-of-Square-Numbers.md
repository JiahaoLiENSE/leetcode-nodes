### 633. Sum of Square Numbers

#### Description
`Given a non-negative integer c, decide whether there're two integers a and b such that a2 + b2 = c.`  

Input: `c = 5`  
Output: `true`  
Explanation: `1 * 1 + 2 * 2 = 5`  

Input: `c = 3`  
Output: `false`  

#### Java

```java
class Solution {
    public boolean judgeSquareSum(int c) {
        int i = 0, j = (int) Math.sqrt(c);
        while(i<j) {
            int sum = i * i + j * j;
            if(sum > c) {
                j--;
            } else if(sum < c) {
                i++;
            } else {
                return true;
            }
        }
        return false;
    }
}
```

#### JavaScript

```javascript
/**
 * @param {number} c
 * @return {boolean}
 */
var judgeSquareSum = function(c) {
    let i = 0;
    let j = Math.floor(Math.sqrt(c)); // ~~Math.sqrt(c)
    while(i<=j) {
        let sum = i*i + j*j;
        if(sum === c) {
            return true;
        } else if(sum > c) {
            j--;
        } else {
            i++;
        }
    }
    return false;
};

```
