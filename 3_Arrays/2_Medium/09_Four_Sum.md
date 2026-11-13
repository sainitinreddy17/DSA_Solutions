# 4 Sum

## Brute Approach :

- For getting quadruplets, 4 nested loops will be used.

- The first loop(say i) will run from 0 to n-1. Inside which, there will be the second loop(say j) that will run from i+1 to n-1. The third loop(say k) that runs from j+1 to n-1. Inside loop k, the fourth loop(say l) will run from k+1 to n-1, yielding 4 elements from array for considering a quadruplet.

- Now, inside these four nested loops, check the sum of arr[i], arr[j], arr[k] and arr[l], and if it is equal to the target, sort this quadruplet and insert it in the set data structure declared to store ans. Finally, return a list of stored quadruplets.

```Java
//function to find quadruplets having sum equal to target
    public List<List<Integer>> fourSum(int[] nums, int target) {
        //size of the array
        int n = nums.length;
        
        // Set to store unique quadruplets
        Set<List<Integer>> set = new HashSet<>();
        
        // Checking all possible quadruplets
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                for (int k = j + 1; k < n; k++) {
                    for (int l = k + 1; l < n; l++) {
                        // Calculate the sum of the current quadruplet
                        long sum = nums[i] + nums[j] + nums[k] + nums[l];
                        
                        // Check if the sum matches the target
                        if (sum == target) {
                            List<Integer> temp = Arrays.asList(nums[i], nums[j], nums[k], nums[l]);
                            // Sort the quadruplet to ensure uniqueness
                            Collections.sort(temp);
                            set.add(temp);
                        }
                    }
                }
            }
        }
        
        // Convert set to list (unique quadruplets)
        return new ArrayList<>(set);
    }
```

## Complexity Analysis :

- Time Complexity: O(N^4)
- Space Complexity: O(2 x no. of the quadruplets)
