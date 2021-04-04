### 665. Non-decreasing Array
#### Description
```
Given an array nums with n integers, your task is to check if it could become non-decreasing
by modifying at most one element.

We define an array is non-decreasing if nums[i] <= nums[i + 1] holds for every i (0-based)
such that (0 <= i <= n - 2).
```

#### Example
```
Input: nums = [4,2,3]
Output: true
Explanation: You could modify the first 4 to 2 to get a non-decreasing array.
```

```
Input: nums = [4,2,1]
Output: false
Explanation: You can't get a non-decreasing array by modify at most one element.
```
#### Java
```java
// It is equal list or increasing list.
// check if current nums[i] greater or less than previous nums[i-1];
// if less, compare current with nums[i-2],
// if current is less than nums[i-2], make nums[i-1] value smaller(move it down same as nums[i] does);
// if greater than, make current larger(move it up same as nums[i-1] does).
// if count of modification is over 1, done the process.
class Solution {
    public boolean checkPossibility(int[] nums) {
        if(nums.length == 0) {
            return false;
        }
        if (nums.length <= 1)
			    return true;
        
        int count = 0;
        for(int i = 1; i < nums.length; i++) {
            if(nums[i] < nums[i-1]) {
                if(i == 1 || nums[i-2] <= nums[i]) {
                    nums[i-1] = nums[i];
                    count++;
                } else {
                    nums[i] = nums[i-1];
                    count++;
                }
            }
        }
        return count <= 1;
        
    }
}
```

#### Python
```python
class Solution:
    def checkPossibility(self, nums: List[int]) -> bool:
        if len(nums) == 0:
            return False
        
        count = 0
        for i in range(1, len(nums)):
            if nums[i] < nums[i-1]:
                if i == 1 or nums[i-2] <= nums[i]:
                    nums[i-1] = nums[i]
                    count +=1
                else:
                    nums[i] = nums[i-1]
                    count +=1
        return count <= 1
```
