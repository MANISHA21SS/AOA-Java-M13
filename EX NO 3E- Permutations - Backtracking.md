
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 01/05/26
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1.Start and read the array of numbers.

2.Use a recursive backtracking function to build permutations.

3.At each step, add an unused element to the current list.

4.When the current list size equals the array length, add it to the result.

5.Backtrack by removing the last element and continue until all permutations are generated  

## Program:
```
/*
Developed by: Manisha selvakumari.S.S. 
Register Number: 212223220055 
*/
import java.util.Scanner;

public class Main {

    // Function to count valid distributions
    static int countWays(int n, int limit) {

        int count = 0;

        // Try all possible candies for 3 children
        for (int i = 0; i <= limit; i++) {
            for (int j = 0; j <= limit; j++) {
                int k = n - (i + j);

                // Check valid distribution
                if (k >= 0 && k <= limit) {
                    count++;
                }
            }
        }

        return count;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int limit = sc.nextInt();

        int result = countWays(n, limit);

        System.out.println("Number of ways to distribute candies: " + result);
    }
}
```

## Output:

<img width="1164" height="159" alt="image" src="https://github.com/user-attachments/assets/a075785a-f8a0-4bd1-a61b-1df565ebaa33" />


## Result:
The program successfully implemented and the expected output is verified.
