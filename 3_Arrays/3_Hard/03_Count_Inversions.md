# Count Inversions

## Brute Approach :

- Iterate in array from 0 to N-1 to select the first element in the pair. As index j should be greater than index i, inside loop i, run another loop i.e. j from i+1 to N-1. Inside this second loop, check if arr[i] is greater than arr[j] i.e. if arr[i] and arr[j] can be an inversion pair. If it satisfy the condition, increase the count by 1.

- Finally, return the count i.e. the number of such pairs.

```Java
public long numberOfInversions(int[] nums) {
        
        // Size of the array
        int n = nums.length;
 
        // Count the number of pairs
        long cnt = 0;
 
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                
                /* If nums[i] is greater than nums[j], increase count by 1*/
                if (nums[i] > nums[j]) {
                    cnt++;
                }
            }
        }
        // Return the count of inversions
        return cnt;
    }
```