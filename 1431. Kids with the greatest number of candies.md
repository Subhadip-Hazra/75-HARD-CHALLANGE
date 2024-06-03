# Kids With the Greatest Number of Candies

## Problem Statement

There are `n` kids with candies. You are given an integer array `candies`, where each `candies[i]` represents the number of candies the `i-th` kid has, and an integer `extraCandies`, denoting the number of extra candies that you have.

Return a boolean array `result` of length `n`, where `result[i]` is `true` if, after giving the `i-th` kid all the `extraCandies`, they will have the greatest number of candies among all the kids, or `false` otherwise.

Note that multiple kids can have the greatest number of candies.

### Example 1

- **Input:** `candies = [2, 3, 5, 1, 3]`, `extraCandies = 3`
- **Output:** `[true, true, true, false, true]`
- **Explanation:** 
  - Kid 1 will have 2 + 3 = 5 candies, which is the greatest among the kids.
  - Kid 2 will have 3 + 3 = 6 candies, which is the greatest among the kids.
  - Kid 3 will have 5 + 3 = 8 candies, which is the greatest among the kids.
  - Kid 4 will have 1 + 3 = 4 candies, which is not the greatest among the kids.
  - Kid 5 will have 3 + 3 = 6 candies, which is the greatest among the kids.

### Example 2

- **Input:** `candies = [4, 2, 1, 1, 2]`, `extraCandies = 1`
- **Output:** `[true, false, false, false, false]`
- **Explanation:** There is only 1 extra candy.
  - Kid 1 will always have the greatest number of candies, even if a different kid is given the extra candy.

### Example 3

- **Input:** `candies = [12, 1, 12]`, `extraCandies = 10`
- **Output:** `[true, false, true]`

### Constraints

- `n == candies.length`
- `2 <= n <= 100`
- `1 <= candies[i] <= 100`
- `1 <= extraCandies <= 50`

## Intuition and Approach

### Intuition

To determine if a kid will have the greatest number of candies after receiving extra candies, we need to compare the potential new total of each kid's candies with the current maximum number of candies. If the new total is greater than or equal to the current maximum, that kid will indeed have the greatest number of candies.

### Approach

1. **Find the Current Maximum Candies:**
   - Traverse the array `candies` to find the maximum number of candies any kid currently has.

2. **Calculate Potential New Total:**
   - For each kid, add `extraCandies` to their current candies.
   - Compare this new total with the previously found maximum candies.
   - If the new total is greater than or equal to the maximum, append `true` to the result list; otherwise, append `false`.

### Time Complexity

- **Finding Maximum Candies:** \(O(n)\), where \(n\) is the number of kids.
- **Calculating New Totals and Comparing:** \(O(n)\).

Overall, the time complexity is **\(O(n)\)**.

### Space Complexity

- **Result List:** \(O(n)\) to store the boolean values for each kid.

Thus, the space complexity is **\(O(n)\)**.

## Solution Code

```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        ArrayList<Boolean> res = new ArrayList<>();
        int max = -1;
        
        // Finding the maximum number of candies any kid currently has
        for(int candy : candies){
            if(max < candy){
                max = candy;
            }
        }
        
        // Checking if each kid can have the greatest number of candies after adding extraCandies
        for(int candy : candies){
            res.add(candy + extraCandies >= max);
        }
        
        return res;
    }
}
```
```javascript
/**
 * @param {number[]} candies
 * @param {number} extraCandies
 * @return {boolean[]}
 */
var kidsWithCandies = function(candies, extraCandies) {
    let res = [];
    let max = Math.max(...candies);
    
    for(let candy of candies ){
        res.push(candy + extraCandies >= max );
    }
    return res;
};

```

## Dry Run

Let's go through a dry run of the given solution with the example:

### Example

**Input:** `candies = [2, 3, 5, 1, 3]`, `extraCandies = 3`  
**Output:** `[true, true, true, false, true]`

### Steps

1. **Initial Setup:**
   - `candies = [2, 3, 5, 1, 3]`
   - `extraCandies = 3`
   - Initialize `res` as an empty list: `res = []`
   - Initialize `max` as `-1`: `max = -1`

2. **Finding the Maximum Number of Candies:**
   - Traverse through the `candies` array:
     - For `candy = 2`: 
       - `max = max(-1, 2) = 2`
     - For `candy = 3`: 
       - `max = max(2, 3) = 3`
     - For `candy = 5`: 
       - `max = max(3, 5) = 5`
     - For `candy = 1`: 
       - `max = max(5, 1) = 5`
     - For `candy = 3`: 
       - `max = max(5, 3) = 5`
   - Final `max` value after traversal: `max = 5`

3. **Calculate Potential New Total and Compare:**
   - Traverse through the `candies` array again:
     - For `candy = 2`: 
       - New total = `2 + 3 = 5`
       - Compare with `max`: `5 >= 5` → `true`
       - Append `true` to `res`: `res = [true]`
     - For `candy = 3`: 
       - New total = `3 + 3 = 6`
       - Compare with `max`: `6 >= 5` → `true`
       - Append `true` to `res`: `res = [true, true]`
     - For `candy = 5`: 
       - New total = `5 + 3 = 8`
       - Compare with `max`: `8 >= 5` → `true`
       - Append `true` to `res`: `res = [true, true, true]`
     - For `candy = 1`: 
       - New total = `1 + 3 = 4`
       - Compare with `max`: `4 < 5` → `false`
       - Append `false` to `res`: `res = [true, true, true, false]`
     - For `candy = 3`: 
       - New total = `3 + 3 = 6`
       - Compare with `max`: `6 >= 5` → `true`
       - Append `true` to `res`: `res = [true, true, true, false, true]`

4. **Final Result:**
   - The result list `res` is `[true, true, true, false, true]`

This dry run demonstrates how the algorithm works step-by-step, ensuring we understand how the solution is derived.
