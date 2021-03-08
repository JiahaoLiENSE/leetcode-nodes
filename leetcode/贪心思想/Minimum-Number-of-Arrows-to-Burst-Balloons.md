### 452. Minimum Number of Arrows to Burst Balloons
#### Description
`There are some spherical balloons spread in two-dimensional space. For each balloon, provided input is the start and end coordinates of the horizontal diameter. Since it's horizontal, y-coordinates don't matter, and hence the x-coordinates of start and end of the diameter suffice. The start is always smaller than the end.`  

`An arrow can be shot up exactly vertically from different points along the x-axis. A balloon with xstart and xend bursts by an arrow shot at x if xstart ≤ x ≤ xend. There is no limit to the number of arrows that can be shot. An arrow once shot keeps traveling up infinitely.`  
`Given an array points where points[i] = [xstart, xend], return the minimum number of arrows that must be shot to burst all balloons.`  
#### Example
Input: `points = [[10,16],[2,8],[1,6],[7,12]]`  
Output: `2`  
Explanation: `One way is to shoot one arrow for example at x = 6 (bursting the balloons [2,8] and [1,6]) and another arrow at x = 11 (bursting the other two balloons).`  

Input: `points = [[1,2],[3,4],[5,6],[7,8]]`  
Output: `4`

Input: `points = [[1,2],[2,3],[3,4],[4,5]]`  
Output: `2`  
#### Java
```java
# Find non-overlapping intervals is the min number of arrows that must be shot to burst all balloons.
class Solution {
    public int findMinArrowShots(int[][] points) {
        if(points.length == 0) return 0;
        Arrays.sort(points, Comparator.comparingInt(o -> o[1]));
        int overLaps = 0;
        int nonOverLaps = 0;
        int left = 0, right = 1;
        while(right < points.length) {
            if(points[right][0] <= points[left][1]) {   // compare to two sorted intervals: start element([1][0]) of second intervals in array vs end element([0][1]) of first intervals in array. 
                overLaps++;
            } else {
                left = right;
            }
            right++;
        }
        nonOverLaps = points.length - overLaps;
        return nonOverLaps;
    }
}
```
#### Python
```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        if len(points) == 0:
            return 0
        if len(points) == 1:
            return 1
        points.sort(key = lambda x: x[1])  // For lambda -> https://www.w3schools.com/python/python_lambda.asp
        nonOverLaps = 1
        right = points[0][1]
        for i in range(1, len(points)):
            if points[i][0] <= right:
                continue
            else:
                nonOverLaps += 1
            right = points[i][1]
        return nonOverLaps
```
