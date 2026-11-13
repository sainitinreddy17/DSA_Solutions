# Linear Search 

## Approach :

- The array nums and the integer target are already given to the function, so nothing is read from input.

- Start at index i = 0. Check whether i < nums.size(). If this condition holds true, it means an element remains to be examined, hence compare it with the target.

- Check whether nums[i] == target. If this condition holds true, it means the current element matches and no earlier element matched, hence return i.

- If the equality check is false, it means the current element is not the target, hence increase i by one and repeat the checks.

- If the loop ends without returning an index, it means every element failed to match. The target being absent is the only remaining possibility, hence return -1.

```Java
int linearSearch(vector<int>& nums, int target) {
        // Examine elements from left to right.
        for (int i = 0; i < (int)nums.size(); i++) {
            // Check whether this element matches the target.
            if (nums[i] == target) {
                // Return the smallest matching index.
                return i;
            }
        }
 
        // No element matched the target.
        return -1;
    }
```

### Complexity Analysis :

- Time Complexity: O(N)
- Space Complexity: O(1)

------

