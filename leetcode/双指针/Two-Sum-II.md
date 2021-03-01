### 167. Two Sum II - Input array is sorted
#### Description:
`Given an array of integers numbers that is already sorted in ascending order, find two numbers such that they add up to a specific target number. Return the indices of the two numbers (1-indexed) as an integer array answer of size 2, where 1 <= answer[0] < answer[1] <= numbers.length.`  

Input: `numbers = [2,7,11,15], target = 9`  
Output: `[1,2]`    
Explanation: `The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.`  

#### Java
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int i = 0;
        int j = numbers.length - 1;
        while(i < j) {
            int sum = numbers[i] + numbers[j];
            if(sum == target) {
                return new int [] {i+1, j+1};
            } else if(sum > target) {
                j--;
            } else {
                i++;
            }
        }
        return null;
    }
}
```

#### JavaScript
```javascript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
    if(numbers == null) return null;
    let i = 0;
    let j = numbers.length - 1;
    let result = [];
    while(i<j) {
        let sum = numbers[i] + numbers[j];
        if(sum === target) {
            result.push(i+1);
            result.push(j+1);
            break;
        } else if(sum > target) {
            j--;
        } else {
            i++;
        }
    }
    return result;
};
```

#### Python
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        i = 0
        j = len(numbers) - 1
        while i<j:
            sum = numbers[i] + numbers[j]
            if sum == target:
                return [i+1, j+1]
            elif sum > target:
                j -= 1
            else:
                i += 1
        return null
```
