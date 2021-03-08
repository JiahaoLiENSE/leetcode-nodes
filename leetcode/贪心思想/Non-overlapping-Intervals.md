### 435. Non-overlapping Intervals
#### Description
`Given a collection of intervals, find the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.`  

#### Example
Input: `[[1,2],[2,3],[3,4],[1,3]]`  
Output: `1`  
Explanation: `[1,3] can be removed and the rest of intervals are non-overlapping.`  

Input: `[[1,2],[1,2],[1,2]]`  
Output: `2`  
Explanation: `You need to remove two [1,2] to make the rest of intervals non-overlapping.`  

#### Java
```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if(intervals.length == 0) {
            return 0;
        }
        
        Arrays.sort(intervals, Comparator.comparingInt(o -> o[1]));
        int overLapping = 0;
        int left = 0;
        int right = 1;
        while(right < intervals.length) {
            if(intervals[right][0] < intervals[left][1]) {
                overLapping++;
            } else {
                left = right;
            }
            right++;
        }
        return overLapping;
    }
    
    /* Another Comparator method
    void sort(int[][] nums) {  //sort the array by ending point
        Arrays.sort(nums, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[1] - o2[1];
            }
        });
    }
    */
}
```
#### Python
```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        if len(intervals) == 0:
            return 0
        intervals.sort(key = lambda x : x[1])
        overLaps = 0
        left = 0
        right = 1
        for i in range(right, len(intervals)):
            if intervals[right][0] < intervals[left][1]:
                overLaps += 1
            else:
                left = right
            right += 1
        return overLaps
```
