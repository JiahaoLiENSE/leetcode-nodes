### 75. Sort Colors

#### Description
`Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.`  
`We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.`  

#### Example
Input: `nums = [2,0,2,1,1,0]`  
Output: `[0,0,1,1,2,2]`  

Input: `nums = [2,0,1]`  
Output: `[0,1,2]`  

#### Java
```java
class Solution {
    public void sortColors(int[] nums) {
        int red = 0, blue = nums.length - 1;
        int white = 0; // As a counter
        while(white <= blue) {
            if(nums[white] == 0) {
                swap(nums, red, white);
                white++;
                red++;
            } else if(nums[white] == 2) {
                swap(nums, blue, white);
                blue--;
            } else {
                white++;
            }
        }
    }
    
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
#### Python
```python
class Solution: 
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        red = 0
        blue = len(nums) - 1
        white = 0
        while white <= blue:
            if nums[white] == 0:
                nums[white], nums[red] = nums[red], nums[white]
                red += 1
                white += 1
            elif nums[white] == 2:
                nums[white], nums[blue] = nums[blue], nums[white]
                blue -= 1
            else:
                white += 1
```
