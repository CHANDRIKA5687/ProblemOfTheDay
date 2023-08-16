# ProblemOfTheDay
<h1>Nth catalan number using Java </h1>
Given a number N. The task is to find the Nth catalan number.
The first few Catalan numbers for N = 0, 1, 2, 3, … are 1, 1, 2, 5, 14, 42, 132, 429, 1430, 4862, …

Catalan Number for N is equal to the number of expressions containing N pairs of paranthesis that are correct matched, i.e., for each of the N '(' there exist N ')' on there right and vice versa.

Since answer can be huge return answer modulo 1e9+7.

Note: Positions start from 0 as shown above.

Example 1:

Input:
N = 5
Output: 42
Example 2:

Input:
N = 4
Output: 14
Your Task:
Complete findCatalan() function that takes n as an argument and returns the Nth Catalan number. The output is printed by the driver code.

Expected Time Complexity: O(N^2).
Expected Auxiliary Space: O(N).

Constraints:
1 <= N <= 103

<h1>Solution In Java</h1>

//{ Driver Code Starts
import java.io.*;
import java.util.*;

class GFG {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int t;
        t = Integer.parseInt(br.readLine());
        while(t-- > 0){
            
            int n;
            n = Integer.parseInt(br.readLine());
            
            Solution obj = new Solution();
            int res = obj.findCatalan(n);
            
            System.out.println(res);
            
        }
    }
}

// } Driver Code Ends

class Solution {
    static final int MOD = (int)1e9 + 7;

    public static int findCatalan(int n) {
        int[] catalan = new int[n + 1];
        catalan[0] = 1;
        
        for (int i = 1; i <= n; i++) {
            catalan[i]=0;
            for (int j = 0; j < i; j++) {
                catalan[i] = (catalan[i] + (int)(((long)catalan[j] * catalan[i - j - 1]) % MOD)) % MOD;
            }
        }
        
        return catalan[n];
    }
}
