# June-18
## 826. Most Profit Assigning Work
```java
class Solution {
    private int getMaxProfit(int[][] arr, int ability) {
        int low = 0, high = arr.length - 1;
        int profit=0;
        while (low <= high) {
            int mid = (low + high) / 2;
            if(arr[mid][0]<=ability)
            {
                profit=Math.max(profit,arr[mid][1]);
                low=mid+1;
            }else high=mid-1;
        }return profit;
        
    }

    public int maxProfitAssignment(int[] difficulty, int[] profit, int[] worker) {
        int n = difficulty.length;
        // array that stores diff,profit
        int[][] arr = new int[n][2];
        for (int i = 0; i < n; i++)
            arr[i] = new int[] { difficulty[i], profit[i] };
        Arrays.sort(arr, new Comparator<int[]>() {
            public int compare(int[] a, int[] b) {
                if (a[0] == b[0])
                    return a[1] - b[1];
                return a[0] - b[0];
            }
        });
        for (int i = 1; i < n; i++) {
            arr[i][1] = Math.max(arr[i][1], arr[i - 1][1]);
        }
        int totalProfit = 0;
        for (int ability : worker) {
            totalProfit+=getMaxProfit(arr, ability);  
        }
        return totalProfit;
    }
}
