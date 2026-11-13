# Three Sum

## Brute Approach :

- Declare a set to store unique triplets that sum up to zero.

- Use three nested loops to consider every possible triplet in the array:
    * Outer loop i runs from 0 to n-3.
    * Middle loop j runs from i+1 to n-2.
    * Inner loop k runs from j+1 to n-1.

- For each triplet (nums[i], nums[j], nums[k]), check if their sum equals zero.

- If yes, sort the triplet to maintain a consistent order and insert it into the set to avoid duplicates.

- After processing all triplets, convert the set into a vector and return it as the final result.

```Java
 public List<List<Integer>> threeSum(int[] nums) {
        // Set to store unique triplets
        Set<List<Integer>> tripletSet = new HashSet<>();
 
        int n = nums.length;
 
        // Check all possible triplets
        for (int i = 0; i < n - 2; i++) {
            for (int j = i + 1; j < n - 1; j++) {
                for (int k = j + 1; k < n; k++) {
                    if (nums[i] + nums[j] + nums[k] == 0) {
                        // Found a triplet that sums up to target
                        List<Integer> temp = new ArrayList<>();
                        temp.add(nums[i]);
                        temp.add(nums[j]);
                        temp.add(nums[k]);
                        
                        /* Sort the triplet to ensure 
                        uniqueness when storing in set*/
                        Collections.sort(temp);
                        tripletSet.add(temp);
                    }
                }
            }
        }
 
        // Convert set to list of lists (unique triplets)
        List<List<Integer>> ans = new ArrayList<>(tripletSet);
 
        //Return the ans
        return ans;
    }
```

## Complexity Analysis :

- Time Complexity: O(N^3 x log(no. of unique triplets))
- Space Complexity: O(2 x no. of the unique triplets)

---------------------


