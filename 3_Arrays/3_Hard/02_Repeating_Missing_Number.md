# Find the repeating and missing number

## Brute Approach : 

- Iterate in array from 1 to N & for each integer, i, count its occurrence in the given array using linear search.

- Store those two elements that have the occurrence of 2 and 0. Finally, return the elements.

```Java
// Function to find repeating and missing numbers
    public int[] findMissingRepeatingNumbers(int[] nums) {
        int n = nums.length; // Size of the array
        int repeating = -1, missing = -1;
 
        // Find the repeating and missing number:
        for (int i = 1; i <= n; i++) {
            // Count the occurrences:
            int cnt = 0;
            for (int j = 0; j < n; j++) {
                if (nums[j] == i) cnt++;
            }
            // Check if i is repeating or missing
            if (cnt == 2) repeating = i;
            else if (cnt == 0) missing = i;
            /* If both repeating and missing are found, break out of loop*/
            if (repeating != -1 && missing != -1)
                break;
        }
        // Return {repeating, missing}
        return new int[] {repeating, missing};
    }
```

## Complexity Analysis :

- Time Complexity: O(N^2)
- Space Complexity: O(1)

------

## Better Approach : 

- The range of the number is 1 to N, so declare a hash array of size N+1 (as we want to store the frequency of N as well).

- Iterate all the elements of the given array and update the hash array when an element is encountered.

- Now, iterate in the hash array and return the two elements with frequencies 2 and 0.

```Java
 // Function to find repeating and missing numbers
    public int[] findMissingRepeatingNumbers(int[] nums) {
        
        // Size of the array
        int n = nums.length;
        
        // Hash array to count occurrences
        int[] hash = new int[n + 1];
        
        // Update the hash array:
        for (int i = 0; i < n; i++) {
            hash[nums[i]]++;
        }
 
        int repeating = -1, missing = -1;
        
        // Find the repeating and missing number:
        for (int i = 1; i <= n; i++) {
            if (hash[i] == 2) {
                repeating = i;
            } else if (hash[i] == 0) {
                missing = i;
            }
            /* If both repeating and missing are found, break out of loop*/
            if (repeating != -1 && missing != -1) {
                break;
            }
        }
        // Return [repeating, missing]
        return new int[]{repeating, missing};
    }
```

## Complexity Analysis :

- Time Complexity: O(2*N)
- Space Complexity: O(N)
