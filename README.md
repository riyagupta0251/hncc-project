import java.util.*;


public class MatrixOperation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the number of rows in the matrix1: ");
        int rows = scanner.nextInt();
        System.out.print("Enter the number of columns in the matrix1: ");
        int coloumns = scanner.nextInt();
       
        double[][] matrix1 = new double[rows][coloumns];

        System.out.println("Enter the elements of matrix1: ");
        for(int i=0;i<rows;i++){
            for(int j=0; j<coloumns; j++){
                matrix1[i][j]= scanner.nextDouble();
            }
            System.out.println("\n");
        }
        System.out.println("Matrix :" + matrix1);
       
double determinant = calculateDeterminant(matrix1);
System.out.println("Determinant"+ determinant);
if(determinant == 0){
    System.out.println("Matrix is not invertible");

}else{
    double[][] inverseMatrix = calculateInverse(matrix1);
    System.out.println("Inverse Matrix");
    printMatrix(inverseMatrix);

}
    scanner.close();

    }
    public static void printMatrix(double[][] matrix1){
        int rows = matrix1.length;
        int coloumns = matrix1[0].length;

        for(int i=0;i<rows;i++){
            for(int j=0; j<coloumns; j++){
                System.out.print(matrix1[i][j]+ " ");

            }
            System.out.println();
        }
    }
    public static double calculateDeterminant(double[][] matrix1){
        int rows = matrix1.length;
        int coloumns = matrix1[0].length;
       
        if(rows != coloumns){
      throw new IllegalArgumentException("Matrix must be square");
        }
        if(rows == 1 ){
            return matrix1[0][0];
        }
        double determinant =0;

        for(int i=0; i<rows; i++){
            double[][] subMatrix = new double[rows-1][coloumns-1];
            for(int j=1; j<rows; j++){
                for(int k=0, l=0; k<coloumns; k++){
                    if(k!=i){
                        subMatrix[j-1][l]= matrix1[j][k];
                        l++ ;
                    }
                }
            }
            determinant += Math.pow(-1, i)*matrix1[0][i]*calculateDeterminant(subMatrix);
        }
        return determinant;
    }
    public static double[][] calculateInverse(double[][] matrix1){
     int rows = matrix1.length;
     int coloumns = matrix1[0].length;

     if(rows != coloumns){
        throw new IllegalArgumentException("Matrix must be square");
     }
     double determinant = calculateDeterminant(matrix1);
     if(determinant == 0){
        throw new IllegalArgumentException("Matrix is not invertible");
     }
     double[][] adjugateMatrix = calculateAdjugate(matrix1);
     double [][] inverseMatrix = new double[rows][coloumns];
     for(int i=0; i<rows; i++){
        for(int j=0; j<coloumns; j++){
            inverseMatrix[i][j] = -adjugateMatrix[i][j]/determinant;
        }
     }
     return inverseMatrix;
    }
    public static double[][] calculateAdjugate(double[][] matrix1){
        int rows = matrix1.length;
        int coloumns = matrix1[0].length;

        double[][] adjugateMatrix = new double[rows][coloumns];
        for(int i=0; i<rows; i++){
            for(int j=0;j<coloumns; j++){
            double[][] subMatrix = new double[rows-1][coloumns-1];
            for(int k=0,m=0; k<rows; k++){
                if(k!=i){
                    for(int l=0,n=0; l<coloumns; l++){
                        if(l != j){
       subMatrix[m][n] = matrix1[k][l];
       n++;
                        }
                    }
                    m++;
                }
               
            }
            double cofactor = Math.pow(-1, i+j)*calculateDeterminant(subMatrix);
            adjugateMatrix[i][j] = cofactor;
        }
       

    }
    return adjugateMatrix;
}

}
