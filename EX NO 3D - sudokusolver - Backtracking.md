
# EX 3D Sudoku solver - Backtracking.
## DATE:
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1.Start and read the 9×9 Sudoku grid (use 0 for empty cells).

2.Find the next empty cell in the board.

3.Try placing digits 1–9 and check if placement is safe (row, column, and 3×3 box).

4.If safe, place the number and recursively solve the next cell; if not, backtrack.

5.Continue until the board is completely filled and display the solved Sudoku.
## Program:
```
/*
Developed by: Manisha selvakumari.S.S.
Register Number: 212223220055 
*/
import java.util.Scanner;

public class Main {

    static final int SIZE = 4;

    // Check whether placing num is safe
    static boolean isSafe(char[][] board, int row, int col, char num) {

        // Check row and column
        for (int i = 0; i < SIZE; i++) {

            if (board[row][i] == num)
                return false;

            if (board[i][col] == num)
                return false;
        }

        // Check 2x2 subgrid
        int startRow = row - row % 2;
        int startCol = col - col % 2;

        for (int i = startRow; i < startRow + 2; i++) {
            for (int j = startCol; j < startCol + 2; j++) {

                if (board[i][j] == num)
                    return false;
            }
        }

        return true;
    }

    // Backtracking solver
    static boolean solveSudoku(char[][] board) {

        for (int row = 0; row < SIZE; row++) {

            for (int col = 0; col < SIZE; col++) {

                // Empty cell
                if (board[row][col] == '.') {

                    for (char num = '1'; num <= '4'; num++) {

                        if (isSafe(board, row, col, num)) {

                            board[row][col] = num;

                            if (solveSudoku(board))
                                return true;

                            // Backtrack
                            board[row][col] = '.';
                        }
                    }

                    return false;
                }
            }
        }

        return true;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        char[][] board = new char[SIZE][SIZE];

        // Read exactly 4 lines
        for (int i = 0; i < SIZE; i++) {

            if (!sc.hasNextLine()) {
                System.out.println("No solution exists.");
                return;
            }

            String line = sc.nextLine().trim();

            // Validate row length
            if (line.length() != SIZE) {
                System.out.println("No solution exists.");
                return;
            }

            board[i] = line.toCharArray();
        }

        if (solveSudoku(board)) {

            System.out.println("Solved board:");

            for (int i = 0; i < SIZE; i++) {

                for (int j = 0; j < SIZE; j++) {

                    System.out.print(board[i][j]);

                    if (j < SIZE - 1)
                        System.out.print(" ");
                }

                System.out.println();
            }

        } else {
            System.out.println("No solution exists.");
        }
    }
}
```

## Output:

<img width="1130" height="497" alt="image" src="https://github.com/user-attachments/assets/fd50ddc0-3b7b-46d2-83fe-4a1fc3ce2ca6" />



## Result:
The program successfully implemented and the expected output is verified.
