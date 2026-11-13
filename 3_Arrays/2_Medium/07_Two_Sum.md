# Two Sum

## Brute Approach : 

- Iterate in array from 0 to last index of the array (lets call this variable i). Now, run another loop say(j) from i+1 to last index of the array.

- If sum of arr[i] and arr[j] equals to target then return the i and j. If no such indices are found then return -1 and -1.

```Java
 public int[] twoSum(int[] nums, int target) {
        
        int n = nums.length;
        //create ans array to store ans
        int[] ans = new int[2];
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                
                /* if nums[i] + nums[j] is equal to 
                   target put i and j in ans */
                if (nums[i] + nums[j] == target) {
                    ans[0] = i;
                    ans[1] = j;
                    return ans;
                }
                
            }
        }
        
        // Return {-1, -1} if no such pair is found
        return new int[]{-1, -1};
    }
```

## Complexity Analysis : 

- Time Complexity:O(N^2)
- Space Complexity: O(1)


---------------------


## Optimal Approach : 

- Sort the given array and initialize two pointers i.e. left, which points to the 0th index, and right, which points to the last index.
- Now, using a loop, check the sum of arr[left] and arr[right] until left less than right.
    * If sum of arr[left] and arr[right] greater than target, decrement the right pointer.

    * If sum of arr[left] and arr[right] less than target, increment the left pointer.

    * If sum of arr[left] and arr[right] equals to target, return the result. Finally, if no results are found we will return {-1, -1}.

```Java
 public int[] twoSum(int[] nums, int target) {
        // Size of the nums array
        int n = nums.length;
        
        // Array to store indices of two numbers
        int[] ans = new int[2];
        
        // 2D array to store {element, index} pairs
        int[][] eleIndex = new int[n][2];
        for (int i = 0; i < nums.length; i++) {
            eleIndex[i][0] = nums[i];
            eleIndex[i][1] = i;
        }
        
        /* Sort eleIndex by the first
        element in ascending order*/
        Arrays.sort(eleIndex, new Comparator<int[]>() {
            public int compare(int[] a, int[] b) {
                return Integer.compare(a[0], b[0]);
            }
        });
 
        /* Two pointers: one starting 
        from left and one from right*/
        int left = 0, right = n - 1;
 
        while (left < right) {
            /* Calculate sum of elements at
            left and right pointers*/
            int sum = eleIndex[left][0] + eleIndex[right][0];
 
            if (sum == target) {
                
                /* If sum equals target, 
                store indices and return*/
                ans[0] = eleIndex[left][1];
                ans[1] = eleIndex[right][1];
                return ans;
                
            } else if (sum < target) {
                
                /* If sum is less than target,
                move left pointer to the right*/
                left++;
                
            } else {
                
                /* If sum is greater than target,
                move right pointer to the left*/
                right--;
                
            }
        }
 
        // If no such pair found, return {-1, -1}
        return new int[]{-1, -1};
    }
```

## Complexity Analysis :

- Time Complexity: O(N) + O(N*logN)
- Space Complexity: O(N)