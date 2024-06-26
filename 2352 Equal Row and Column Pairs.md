# Equal Row and Column Pairs

## Problem Statement

Given a 0-indexed \( n \times n \) integer matrix `grid`, return the number of pairs \((r_i, c_j)\) such that row \( r_i \) and column \( c_j \) are equal.

A row and column pair is considered equal if they contain the same elements in the same order (i.e., an equal array).

### Examples


#### Example 1

<img src="https://i.postimg.cc/tRhKTS8R/ex1.jpg" alt="ex1">

- **Input:** `grid = [[3,2,1], [1,7,6], [2,7,7]]`
- **Output:** `1`
- **Explanation:** There is 1 equal row and column pair:
  - (Row 2, Column 1): `[2,7,7]`

#### Example 2

<img src="https://i.postimg.cc/PrTB8bkW/ex2.jpg" alt="ex2">


- **Input:** `grid = [[3,1,2,2], [1,4,4,5], [2,4,2,2], [2,4,2,2]]`
- **Output:** `3`
- **Explanation:** There are 3 equal row and column pairs:
  - (Row 0, Column 0): `[3,1,2,2]`
  - (Row 2, Column 2): `[2,4,2,2]`
  - (Row 3, Column 2): `[2,4,2,2]`

### Constraints

- \( n == grid.length == grid[i].length \)
- \( 1 \leq n \leq 200 \)
- \( 1 \leq grid[i][j] \leq 10^5 \)

## Solutions

### Java Solution

The Java solution involves transposing the grid matrix and then comparing each row with each column to find equal pairs.

```java
import java.util.Arrays;

class Solution {
    public int equalPairs(int[][] grid) {
        int n = grid.length;
        int res = 0;
        int[][] flip = new int[n][n];
        transpose(grid, flip);

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (Arrays.equals(grid[i], flip[j])) res++;
            }
        }
        return res;
    }

    void transpose(int[][] grid, int[][] flip) {
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid.length; j++) {
                flip[i][j] = grid[j][i];
            }
        }
    }
}
```

### JavaScript Solution

The JavaScript solution also transposes the grid and compares each row with each column using a helper function to check for array equality.

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var equalPairs = function(grid) {
    const n = grid.length;
    let res = 0;
    let flip = new Array(n).fill(0).map(() => new Array(n));
    transpose(grid, flip);

    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            if (arraysEqual(grid[i], flip[j])) res++;
        }
    }
    return res;
};

const transpose = (grid, flip) => {
    for (let i = 0; i < grid.length; i++) {
        for (let j = 0; j < grid.length; j++) {
            flip[i][j] = grid[j][i];
        }
    }
};

const arraysEqual = (arr1, arr2) => {
    if (arr1.length !== arr2.length) return false;
    for (let i = 0; i < arr1.length; i++) {
        if (arr1[i] !== arr2[i]) return false;
    }
    return true;
};
```

## Approach

### Intuition

To determine the number of equal row and column pairs in a grid, we can:
1. **Transpose the Grid:** Create a new matrix where each row of the original grid becomes a column in the new matrix.
2. **Compare Rows and Columns:** Compare each row in the original grid with each column in the transposed grid to count the number of equal pairs.

### Steps

1. **Transpose the Matrix:**
   - Create a new matrix `flip` where each element `flip[i][j]` is set to `grid[j][i]`.

2. **Compare Rows and Columns:**
   - For each row `i` in `grid` and each column `j` in `flip`, check if they are equal using a helper function.
   - If they are equal, increment the result counter.

### Time Complexity

- The time complexity of this solution is \( O(n^3) \) because for each of the \( n \) rows, we compare with \( n \) columns, and each comparison takes \( O(n) \) time.

### Space Complexity

- The space complexity is \( O(n^2) \) for storing the transposed grid.

## Example and Dry Run

Let's go through a dry run of both the Java and JavaScript solutions with Example 1:

**Input:** `grid = [[3,2,1], [1,7,6], [2,7,7]]`
**Output:** `1`

### Java Dry Run

**Initialization:**
- `n = 3`
- `res = 0`
- `flip = [[0,0,0], [0,0,0], [0,0,0]]`

**Transpose:**
- `flip = [[3,1,2], [2,7,7], [1,6,7]]`

**Comparison:**
1. Compare `grid[0] = [3,2,1]` with:
   - `flip[0] = [3,1,2]` → Not equal
   - `flip[1] = [2,7,7]` → Not equal
   - `flip[2] = [1,6,7]` → Not equal

2. Compare `grid[1] = [1,7,6]` with:
   - `flip[0] = [3,1,2]` → Not equal
   - `flip[1] = [2,7,7]` → Not equal
   - `flip[2] = [1,6,7]` → Not equal

3. Compare `grid[2] = [2,7,7]` with:
   - `flip[0] = [3,1,2]` → Not equal
   - `flip[1] = [2,7,7]` → Equal → `res = 1`
   - `flip[2] = [1,6,7]` → Not equal

**Result:**
- Return `res = 1`

## Conclusion

The provided solutions efficiently determine the number of equal row and column pairs in a grid by transposing the grid and comparing rows and columns. Both the Java and JavaScript implementations handle the matrix transposition and comparison steps optimally within the constraints.
