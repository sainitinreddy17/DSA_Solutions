# Majority element - II

## Brute Approach : 

- Iterate in the array to select the elements of the array one by one. Now, for each unique element, run another loop and count its occurrence in the given array. If any element occurs more than the floor of (N/3), include it in our answer.

- While traversing if any element that is already included in our answer is found, just skip it. When the answer array size is already 2, break out of loop, as there cant be more than 2 elements.

- Return the answer array or -1 if no such element is found.

```Java
// Function to find majority elements in an array
    public List<Integer> majorityElementTwo(int[] nums) {
        // Size of the array
        int n = nums.length;
        
        // List of answers
        List<Integer> result = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            /* Checking if nums[i] is not 
            already part of the answer */
            
            if (result.size() == 0 || result.get(0) != nums[i]) {
                
                int cnt = 0;
                
                for (int j = 0; j < n; j++) {
                    // counting the frequency of nums[i]
                    if (nums[j] == nums[i]) {
                        cnt++;
                    }
                }
                
                // check if frequency is greater than n/3
                if (cnt > (n / 3)) {
                    result.add(nums[i]);
                }
            }
            
            // if result size is equal to 2 break out of loop
            if (result.size() == 2) {
                break;
            }
        }
        
        // return the majority elements
        return result;
    }
```

## Complexity Analysis :

- Time Complexity: O(N^2)
- Space Complexity: O(1)

-----


## Optimal Approach : 

- Initialize 4 variables: cnt1 & cnt2 for tracking the counts of elements and el1 & el2 for storing the majority of elements.

- Traverse through the given array. If cnt1 is 0 and the current element is not el2 then store the current element of the array as el1 along with increasing the cnt1 value by 1.

- If cnt2 is 0 and the current element is not el1 then store the current element of the array as el2 along with increasing the cnt2 value by 1.

- If the current element and el1 are the same increase the cnt1 by 1 and if the current element and el2 are the same increase the cnt2 by 1.

- Other than all the above cases decrease cnt1 and cnt2 by 1. The integers present in el1 & el2 should be the result we are expecting. So, using another loop, to manually check their counts if they are greater than the floor(N/3).

```Java
// Function to find majority elements in an array
    public List<Integer> majorityElementTwo(int[] nums) {
        
        // Size of the array
        int n = nums.length;

        // Counts for elements el1 and el2
        int cnt1 = 0, cnt2 = 0;
        
        /*Initialize Element 1 and 
        Element 2 with INT_MIN value*/
        int el1 = Integer.MIN_VALUE, el2 = Integer.MIN_VALUE;

        /*Find the potential candidates using
        Boyer Moore's Voting Algorithm*/
        for (int i = 0; i < n; i++) {
            if (cnt1 == 0 && el2 != nums[i]) {
                cnt1 = 1;
                // Initialize el1 as nums[i]
                el1 = nums[i]; 
            } else if (cnt2 == 0 && el1 != nums[i]) {
                cnt2 = 1;
                // Initialize el2 as nums[i]
                el2 = nums[i]; 
            } else if (nums[i] == el1) {
                // Increment count for el1
                cnt1++;
            } else if (nums[i] == el2) {
                // Increment count for el2
                cnt2++; 
            } else {
                // Decrement count for el1
                cnt1--; 
                 // Decrement count for el2
                cnt2--;
            }
        }

        //Validate the candidates by counting occurrences in nums:
        //Reset counts for el1 and el2
        cnt1 = 0; cnt2 = 0; 
        
        for (int i = 0; i < n; i++) {
            if (nums[i] == el1) {
                // Count occurrences of el1
                cnt1++; 
            }
            if (nums[i] == el2) {
                 // Count occurrences of el2
                cnt2++;
            }
        }

        /* Determine the minimum count
        required for a majority element*/
        int mini = n / 3 + 1;
        
        // List of answers
        List<Integer> result = new ArrayList<>(); 

        /*Add elements to the result vector
        if they appear more than n/3 times*/
        if (cnt1 >= mini) {
            result.add(el1);
        }
        if (cnt2 >= mini && el1 != el2) {
            // Avoid adding duplicate if el1 == el2
            result.add(el2); 
        }

        // Uncomment the following line if you want to sort the answer array 
        // Collections.sort(result); // TC --> O(2*log2) ~ O(1);

       //return the majority elements
        return result;
    }
```

## Complexity Analysis :

- Time Complexity: O(N) + O(N)
- Space Complexity: O(1)