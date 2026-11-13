# Print the matrix in spiral manner

## Single Approach : 

- Initialize four variables top as 0, left as 0, bottom as TotalRow - 1, right as TotalColumn - 1.

- Iterate till top is less than or equal to bottom and left less than or equal to right

- For moving left to right use a loop(say i) and add the elements. Increment top by 1.

- For moving top to bottom use another loop and add the elements in answer. Decrement right by 1.

- If top is less than or equal to bottom then for moving right to left use another loop and add the elements in answer. Decrement bottom by 1.

- If left is less than or equal to right the for moving bottom to top take another loop and add the elements in answer. Increment left by 1. Lastly, return the answer.

```Java
//Function to print matrix in spiral manner
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<>();
        
        // Number of rows
        int n = matrix.length;
 
        // Number of columns
        int m = matrix[0].length;
        
        // Initialize pointers for traversal
        int top = 0, left = 0;      
        int bottom = n - 1, right = m - 1;
        
        // Traverse the matrix in spiral order
        while (top <= bottom && left <= right) {
            // Traverse from left to right
            for (int i = left; i <= right; ++i) {
                ans.add(matrix[top][i]);
            }
            top++;
            
            // Traverse from top to bottom
            for (int i = top; i <= bottom; ++i) {
                ans.add(matrix[i][right]);
            }
            right--;
            
            // Traverse from right to left
            if (top <= bottom) {
                for (int i = right; i >= left; --i) {
                    ans.add(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // Traverse from bottom to top
            if (left <= right) {
                for (int i = bottom; i >= top; --i) {
                    ans.add(matrix[i][left]);
                }
                left++;
            }
        }
        
        //Return the ans
        return ans;
    }
```

## Complexity Analysis : 

- Time Complexity: O(N×M)
- Space Complexity: O(1)