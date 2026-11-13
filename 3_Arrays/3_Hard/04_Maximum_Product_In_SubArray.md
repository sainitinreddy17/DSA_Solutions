# Maximum Product Subarray in an Array

## Brute Approach :

- Iterate in the array using i which runs from 0 to sizeOfArray - 1, it will basically identify the starting point of the subarrays.

- Now run an inner loop using j from i+1 to sizeOfArray - 1, it will identify the ending point of the subarrays. Inside this loop, iterate again from i to j and multiply elements present in the chosen range.

- Update the maximum product after each iteration and finally, return it.

```Java
// Function to find maximum product subarray
    public int maxProduct(int[] nums) {
        // Initialize result to minimum possible integer
        int result = Integer.MIN_VALUE;
 
        // Iterate through all subarrays
        for (int i = 0; i < nums.length; i++) {
            for (int j = i; j < nums.length; j++) {
                int prod = 1;
 
                // Calculate product of subarray 
                for (int k = i; k <= j; k++) {
                    prod *= nums[k];
                }
 
                // Update the result with maximum product found
                result = Math.max(result, prod);
            }
        }
 
        // Return the maximum product found
        return result;
    }
```

## Complexity Analysis :

- Time Complexity: O(N^3)
- Space Complexity: O(1)

-----

## Better Approach :

- Iterate in the array using i which starts from 0 and goes till sizeOfArray - 1. Now, iterate in array using an inner loop using j, which starts from i+1 and goes till sizeOfArray - 1. Initialize a variable prod to store product and max to store maximum product.

- Inside this loop, multiply arr[j] to prod variable in each iteration and update the max variable each time. Finally, return max variable as an answer.

```Java
// Function to find maximum product subarray
    public int maxProduct(int[] nums) {
        // Initialize result with first element of nums
        int result = nums[0];
 
        /* Iterate through each element
        as a starting point of subarray */
        for (int i = 0; i < nums.length; i++) {
            // Initialize p with nums[i]
            int p = nums[i];
 
            /* Iterate through subsequent elements
            to form subarrays starting from nums[i] */
            for (int j = i + 1; j < nums.length; j++) {
                
                /* Update result with the
                max of current result and p */
                result = Math.max(result, p);
 
                // Update p by multiplying with nums[j]
                p *= nums[j];
            }
 
            // Update result for subarray ending at nums[i]
            result = Math.max(result, p);
        }
 
        // Return maximum product subarray found
        return result;
    }
```

## Complexity Analysis : 

- Time Complexity: O(N^2)
- Space Complexity: O(1)

-------------------