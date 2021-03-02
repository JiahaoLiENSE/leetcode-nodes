### 215. Kth Largest Element in an Array (Medium)

#### Description
`Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.`  

#### Example
Input: `[3,2,1,5,6,4] and k = 2`  
Output: `5`  

Input: `[3,2,3,1,2,4,5,5,6] and k = 4`  
Output: `4`  

#### Java
```java
/*
排序 ：时间复杂度 O(NlogN)，空间复杂度 O(1)
*/
class Solution {
    public int findKthLargest(int[] nums, int k) {
        if(nums == null) return 1;
        Arrays.sort(nums);
        return nums[nums.length - k];
    }
}

/*
堆 ：时间复杂度 O(NlogK)，空间复杂度 O(K)
*/
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> pq = new PriorityQueue<>(); // 小顶堆
    for (int val : nums) {
        pq.add(val);
        if (pq.size() > k)  // 维护堆的大小为 K
            pq.poll();
    }
    return pq.peek();
}

/*
快速选择(Quick Sort) ：时间复杂度 O(N)，空间复杂度 O(1)
*/
public int findKthLargest(int[] nums, int k) {
    k = nums.length - k;
    int l = 0, h = nums.length - 1;
    while (l < h) {
        int j = partition(nums, l, h);
        if (j == k) {
            break;
        } else if (j < k) {
            l = j + 1;
        } else {
            h = j - 1;
        }
    }
    return nums[k];
}

// More explanation on Partitioning: https://www.geeksforgeeks.org/three-way-partitioning-of-an-array-around-a-given-range/
private int partition(int[] a, int l, int h) {
    int i = l, j = h + 1;
    while (true) {
        while (a[++i] < a[l] && i < h) ;
        while (a[--j] > a[l] && j > l) ;
        if (i >= j) {
            break;
        }
        swap(a, i, j);
    }
    swap(a, l, j);
    return j;
}

private void swap(int[] a, int i, int j) {
    int t = a[i];
    a[i] = a[j];
    a[j] = t;
}
```

#### Python
```python
/*
排序 ：时间复杂度 O(NlogN)，空间复杂度 O(1)
*/
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        nums.sort()
        return nums[-(k)]
        
/*
 快速排序(Quick Sort): 时间复杂度 O(N)，空间复杂度 O(1)
*/
class Solution(object):
    def findKthLargest(self, nums, k):
        
        def qSort(arr):
            if len(arr) <= 1:
                return arr
            try:
                pivot = arr[int(len(arr) / 2) - 1]
            except:
                pivot = arr[0]
            
            low, equal, high = [], [], []
            
            for x in arr:
                if x < pivot:
                    low.append(x)
                elif x > pivot:
                    high.append(x)
                else:
                    equal.append(x)
            return qSort(low) + equal + qSort(high)
                
        
        return qSort(nums)[-(k)]
```
