# Rotate matrix by 90 degrees

## Optimal Approach : 

- Run nested for loop say(i) for row and (j) for column to iterate the matrix and transpose the matrix to change rows to columns and columns to rows.

- Loop again to reverse each row of the matrix. Finally return the matrix.

```Java
public void rotateMatrix(int[][] matrix) {
        int n = matrix.length;
        
        // Transpose the matrix
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {
                
                // Swap elements across the diagonal
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
                
            }
        }
        
        // Reverse each row of the matrix
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n / 2; j++) {
                
                // Swap elements symmetrically
                int temp = matrix[i][j];
                matrix[i][j] = matrix[i][n - 1 - j];
                matrix[i][n - 1 - j] = temp;
                
            }
        }
```

## Complexity Analysis : 

- Time Complexity : O(N^2) +O(N^2)
- Space Complexity : O(1)

