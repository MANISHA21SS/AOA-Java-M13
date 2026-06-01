
# EX 3B Rat in Maze- Backtracking 
## DATE:
## AIM:
To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm

1.Start and read the maze, start point, and destination.

2.Initialize a visited matrix to track visited cells.

3.From the current cell, move in all four directions until hitting a wall.

4.Mark visited cells and recursively explore unvisited reachable positions.

5.If the destination is reached, return true; else return false.

## Program:
```
/*
Developed by: Manisha selvakumari.S.S.
Register Number: 212223220055 
*/
import java.util.Scanner;

public class Main {

    // Recursive function to count expressions
    static int findWays(int[] nums, int index, int target) {

        // Base case
        if (index == nums.length) {
            return target == 0 ? 1 : 0;
        }

        // Add current number
        int add = findWays(nums, index + 1, target - nums[index]);

        // Subtract current number
        int subtract = findWays(nums, index + 1, target + nums[index]);

        return add + subtract;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int target = sc.nextInt();

        int result = findWays(nums, 0, target);

        System.out.println("Output: " + result);
    }
}
```

## Output:

<img width="1153" height="295" alt="image" src="https://github.com/user-attachments/assets/66cbebc0-8ad7-4785-9761-6a28235000a4" />



## Result:
The program successfully implemented and the expected output is verified.
