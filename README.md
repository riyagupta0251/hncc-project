This program performs matrix operations using Java. It allows the user to input the dimensions and elements of a matrix and then performs the following operations:

1. Input: The program prompts the user to enter the number of rows and columns for the matrix. It then takes input for each element of the matrix.

2. Print Matrix: The program displays the entered matrix on the screen.

3. Calculate Determinant: The program calculates the determinant of the entered matrix using the recursive method `calculateDeterminant()`. It first checks if the matrix is square (rows = columns) and throws an exception if it is not. If the matrix is a 1x1 matrix, the determinant is simply the single element. Otherwise, it iterates through the first row, recursively calculates the determinant of the submatrix obtained by excluding the current row and column, and adds the product of the current element, its sign (-1 raised to the power of i), and the determinant of the submatrix to the total determinant.

4. Print Determinant: The program displays the calculated determinant on the screen.

5. Inverse Matrix: If the determinant is non-zero, indicating that the matrix is invertible, the program proceeds to calculate the inverse matrix using the `calculateInverse()` method. It first checks if the matrix is square and throws an exception if it is not or if the determinant is zero. It then calculates the adjugate matrix using the `calculateAdjugate()` method. Finally, it divides each element of the adjugate matrix by the determinant to obtain the inverse matrix.

6. Print Inverse Matrix: The program displays the inverse matrix on the screen.

The program utilizes helper methods such as `printMatrix()`, which prints a given matrix, and `calculateAdjugate()`, which calculates the adjugate matrix of a given matrix.
