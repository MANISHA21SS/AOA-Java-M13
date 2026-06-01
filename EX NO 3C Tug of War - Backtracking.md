
# EX 3C Tug of War problem - Backtracking.
## DATE:
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1.Start and read the array elements.

2.Calculate the total sum of all elements.

3.If the total sum is odd, return false (cannot partition equally).

4.Use dynamic programming to check if any subset sums to totalSum / 2.

5.If such a subset exists, return true; otherwise, return false.   

## Program:
```
/*
Developed by: Manisha selvakumari.S.S.
Register Number: 212223220055 
*/
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main {

    // Check if string has unique characters
    static boolean isUnique(String s) {

        boolean[] seen = new boolean[26];

        for (char ch : s.toCharArray()) {

            if (seen[ch - 'a'])
                return false;

            seen[ch - 'a'] = true;
        }

        return true;
    }

    // Backtracking function
    static int maxLength(List<String> arr, String current, int index) {

        if (!isUnique(current))
            return 0;

        int max = current.length();

        for (int i = index; i < arr.size(); i++) {

            max = Math.max(max,
                    maxLength(arr, current + arr.get(i), i + 1));
        }

        return max;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String input = sc.nextLine();

        // Remove brackets and quotes
        input = input.replace("[", "")
                     .replace("]", "")
                     .replace("\"", "");

        String[] words = input.split(",");

        List<String> arr = new ArrayList<>();

        for (String word : words) {
            arr.add(word.trim());
        }

        int result = maxLength(arr, "", 0);

        System.out.println(result);
    }
}

```

## Output:

<img width="1176" height="202" alt="image" src="https://github.com/user-attachments/assets/ad28f53b-bce5-40b3-8eb8-a01b8740e065" />


## Result:
The program successfully implemented and the expected output is verified.
