# Binary-Search-3

## Problem1 Pow(x,n) 
```Java
// Time Complexity : O(log n)
// Space Complexity : O(1)
// Did this code successfully run on Leetcode : yes
// Any problem you faced while coding this : no

class Solution {
    public double myPow(double x, int n) {
        //base
        if(n == 0)
            return 1;

        //logic
        double result = myPow(x, n/2);
        if(n%2==0){
            return result*result;
        }
        else{
            if(n>0)
                return result * result * x;
            else
                return result * result * (1/x);
        }
    }
}
```

## Problem2 find-k-closest-elements

```Java
// Time Complexity : O(log n + k)
// Space Complexity : O(1)
// Did this code successfully run on Leetcode : yes
// Any problem you faced while coding this : no

class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        //Binary search
        //O(logn+k)
        int low = 0;
        int high = arr.length - k;

        while (low < high) {
            int mid = low + (high - low) / 2;
            int distS = x - arr[mid];
            int distE = arr[mid + k] - x;
            if (distS > distE) {
                low = mid + 1;
            } else {
                high = mid;
            }
        }
        List<Integer> result = new ArrayList<>();
        for (int i = low; i < low + k; i++) {
            result.add(arr[i]);
        }
        return result;
    }
}
```




