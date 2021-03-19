### 121. Best Time to Buy and Sell Stock
#### Description
```
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day 
in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
```
#### Example
```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```
#### Java
```java
// pick first element as current minimum value, and compare and find min
// continue to loop through prices, find the max profit(prices[i] - min)

class Solution {
    public int maxProfit(int[] prices) {
        if(prices.length == 0) return 0;
        int currMin = prices[0];
        int maxProfit = 0;
        for(int i = 1; i < prices.length; i++){
            if(currMin > prices[i]){
                currMin = prices[i];
            } else {
                maxProfit = Math.max(maxProfit, prices[i] - currMin);
            }
        }
        return maxProfit;
    }
}
```
#### Python
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices) == 0:
            return 0
        
        currMin = prices[0]
        maxProfit = 0
        for i in range(1, len(prices)):
            if currMin > prices[i]:
                currMin = prices[i]
            else:
                maxProfit = max(maxProfit, prices[i] - currMin)
        return maxProfit
```
