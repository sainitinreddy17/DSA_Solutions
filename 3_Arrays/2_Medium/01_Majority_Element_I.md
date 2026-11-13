# Majority Element-I

## Brute Approach : 

- Iterate in the array to select the elements of the array one by one. Now, for each element, run another loop and count its occurrence in the given array.

- If any element occurs more than the floor of (N/2), simply return it.

```Java
// Function to find the majority element in an array
    public int majorityElement(int[] nums) {
        
        // Size of the given array
        int n = nums.length;
        
        // Iterate through each element of the array
        for (int i = 0; i < n; i++) {
            
            // Counter to count occurrences of nums[i]
            int cnt = 0; 
            
            // Count the frequency of nums[i] in the array
            for (int j = 0; j < n; j++) {
                if (nums[j] == nums[i]) {
                    cnt++;
                }
            }
            
            // Check if frequency of nums[i] is greater than n/2
            if (cnt > (n / 2)) {
                // Return the majority element
                return nums[i]; 
            }
        }
        
        // Return -1 if no majority element is found
        return -1; 
    }
```

## Complexity Analysis :

- Time Complexity: O(N^2)
- Space Complexity: O(1)

------

## Optimal Approach : 

- Initialize 2 variables: count for tracking the count of elements and element for keeping track of the element we are counting.

- Traverse through the given array. If count is 0 then store the current value of the array as element .

- If the current array value and element are the same increase the count by 1. If they are different decrease the count by 1. The integer present in element should be the result expected.

```Java
// Function to find the majority element in an array
    public int majorityElement(int[] nums) {
        // Size of the given array
        int n = nums.length;
        
        // Count
        int cnt = 0;
        
        // Element
        int el = 0;
        
        // Applying the algorithm
        for (int i = 0; i < n; i++) {
            if (cnt == 0) {
                cnt = 1;
                el = nums[i];
            } else if (el == nums[i]) {
                cnt++;
            } else {
                cnt--;
            }
        }
        
        /* Checking if the stored element
         is the majority element*/
        int cnt1 = 0;
        for (int i = 0; i < n; i++) {
            if (nums[i] == el) {
                cnt1++;
            }
        }
        
        // Return element if it is a majority element
        if (cnt1 > (n / 2)) {
            return el;
        }
        
        // Return -1 if no such element found
        return -1;
    }
```

## Complexity Analysis :

- Time Complexity: O(N) + O(N)
- Space Complexity: O(1)