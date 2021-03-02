### 88. Merge Sorted Array

#### Description

`Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.` 
`The number of elements initialized in nums1 and nums2 are m and n respectively. You may assume that nums1 has a size equal to m + n such that it has enough space to hold additional elements from nums2.`  

#### Example

Input: `nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3`  
Output: `[1,2,2,3,5,6]`  

Input: `nums1 = [1], m = 1, nums2 = [], n = 0`  
Output: `[1]`  


#### Java
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int index1 = m - 1, index2 = n - 1;
        int indexMerge = m + n - 1;
        while (index1 >= 0 || index2 >= 0) {
            if (index1 < 0) {
                nums1[indexMerge--] = nums2[index2--];
            } else if (index2 < 0) {
                nums1[indexMerge--] = nums1[index1--];
            } else if (nums1[index1] > nums2[index2]) {
                nums1[indexMerge--] = nums1[index1--];
            } else {
                nums1[indexMerge--] = nums2[index2--];
            }
        }
    }
}
```

#### Python

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        n3, n1, n2 = m + n - 1, m - 1, n - 1
        while n1 >= 0 and n2 >= 0:
            if nums1[n1] > nums2[n2]:
                nums1[n3] = nums1[n1]
                n3, n1 = n3 - 1, n1 - 1
            else:
                nums1[n3] = nums2[n2]
                n3, n2 = n3 - 1, n2 - 1

        while n2 >= 0:
            nums1[n3] = nums2[n2]
            n3, n2 = n3 - 1, n2 - 1
                
```
