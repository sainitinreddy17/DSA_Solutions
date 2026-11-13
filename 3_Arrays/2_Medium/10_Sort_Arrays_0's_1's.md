# Sort an array of 0's 1's and 2's

## Brute Approach : 

- Sort the array using built-in function for sorting. It will manage to sort the array in optimal time.

```Java
public void sortZeroOneTwo(int[] nums) {
        // Sort the array using Arrays.sort
        Arrays.sort(nums);
    }
```

## Complexity Analysis : 

- Time Complexity: O(NxlogN)
- Space Complexity: O(1)

--------------

## Better Approach : 

- Initialize 3 variables to maintain the count of 0, 1 and 2 & iterate in the array to store the frequencies of the 0's, 1's, 2's in their corresponding variables.

- Perform a 2nd traversal of array, to overwrite the array according to the frequencies, first filling up the indices by 0's, then by 1's and at last by 2's. Finally return the array.

```Java
public void sortZeroOneTwo(int[] nums) {
        int cnt0 = 0, cnt1 = 0, cnt2 = 0;
 
        // Counting the number of 0s, 1s, and 2s in the array
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 0) cnt0++;
            else if (nums[i] == 1) cnt1++;
            else cnt2++;
        }
 
        /* Placing the elements in the original array based on counts */
        // placing 0's
        for (int i = 0; i < cnt0; i++) nums[i] = 0;
 
        // placing 1's
        for (int i = cnt0; i < cnt0 + cnt1; i++) nums[i] = 1; 
        
        // placing 2's
        for (int i = cnt0 + cnt1; i < nums.length; i++) nums[i] = 2;
    }
```

## Complexity Analysis : 

- Time Complexity: O(N)+O(N) = O(2N)
- Space Complexity: O(1)

