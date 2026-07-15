# DSA Practice: GCD of Odd and Even Sums

Part of my ongoing Data Structures & Algorithms practice as I prepare for fresher software engineering roles.

## Problem Statement

Given an integer `n`, compute the GCD (Greatest Common Divisor) of two values:

- **sumOdd**: the sum of the smallest `n` positive odd numbers.
- **sumEven**: the sum of the smallest `n` positive even numbers.

Return the GCD of `sumOdd` and `sumEven`.

### Example 1
Input: n = 4
sumOdd  = 1 + 3 + 5 + 7 = 16
sumEven = 2 + 4 + 6 + 8 = 20
Output: 4
Explanation: GCD(16, 20) = 4

### Example 2
Input: n = 5
sumOdd  = 1 + 3 + 5 + 7 + 9 = 25
sumEven = 2 + 4 + 6 + 8 + 10 = 30
Output: 5
Explanation: GCD(25, 30) = 5

### Constraints

- `1 <= n <= 1000`

## Approach

1. Calculate `sumOdd` and `sumEven` using a simple loop:
   - `2*i - 1` generates the i-th odd number
   - `2*i` generates the i-th even number
2. Apply the **Euclidean Algorithm** to find the GCD of the two sums.

## Solution

```java
class Solution {
    public int gcdOfOddEvenSums(int n) {
        int sumOdd = 0;
        int sumEven = 0;
        
        for (int i = 1; i <= n; i++) {
            sumOdd += (2 * i - 1);
            sumEven += (2 * i);
        }
        
        return gcd(sumOdd, sumEven);
    }
    
    private int gcd(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }
}
```

## Complexity

- **Time Complexity:** O(n) — single loop to compute the sums
- **Space Complexity:** O(1) — constant extra space

## Key Concept

- Sum of first `n` odd numbers = `n²`
- Sum of first `n` even numbers = `n(n+1)`
- Since `GCD(n², n(n+1)) = n`, the answer simplifies directly to `n`

## Tech Stack

- Language: Java
