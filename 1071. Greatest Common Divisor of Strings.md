# 1071. Greatest Common Divisor of Strings 🚀

Given two strings `str1` and `str2`, the task is to find the largest string `x` such that `x` divides both `str1` and `str2`.

## Problem Statement 📝

For two strings `s` and `t`, we say "t divides s" if and only if `s = t + t + t + ... + t + t` (i.e., `t` is concatenated with itself one or more times).

### Examples

#### Example 1
- **Input:** `str1 = "ABCABC"`, `str2 = "ABC"`
- **Output:** `"ABC"`

#### Example 2
- **Input:** `str1 = "ABABAB"`, `str2 = "ABAB"`
- **Output:** `"AB"`

#### Example 3
- **Input:** `str1 = "LEET"`, `str2 = "CODE"`
- **Output:** `""`

### Constraints
- `1 <= str1.length, str2.length <= 1000`
- `str1` and `str2` consist of English uppercase letters.

## Approach 🔍

1. **Concatenation Check:** 
    - If concatenating `str1` and `str2` in both possible orders (`str1 + str2` and `str2 + str1`) does not produce the same result, return an empty string. This check ensures that both strings can be constructed by repeating some common substring.
    
2. **Length and GCD Calculation:**
    - Calculate the lengths of `str1` and `str2`.
    - Compute the GCD of these lengths using the Euclidean algorithm.

3. **Return the GCD Substring:**
    - The substring of `str1` from index 0 to the GCD length is the largest string that divides both `str1` and `str2`.

## Dry Run 🏃‍♂️

### Example: `str1 = "ABCABC"`, `str2 = "ABC"`

1. **Concatenation Check:**
    - `str1 + str2 = "ABCABCABC"`
    - `str2 + str1 = "ABCABCABC"`
    - Both are equal, so continue.

2. **Lengths and GCD Calculation:**
    - `len1 = 6`, `len2 = 3`
    - `gcd(6, 3) = 3`

3. **Return the GCD Substring:**
    - `str1.substring(0, 3) = "ABC"`

## Diagram 🖼️

Here's a diagram illustrating the process:

```
str1 = "ABCABC"
str2 = "ABC"

Step 1: Check concatenation:
    "ABCABC" + "ABC" == "ABC" + "ABCABC"
    "ABCABCABC" == "ABCABCABC" (True)

Step 2: Calculate GCD of lengths:
    len1 = 6
    len2 = 3
    gcd(6, 3) = 3

Step 3: Extract substring of str1 up to GCD length:
    str1.substring(0, 3) = "ABC"
```

## Code Implementation 💻

```java []
//java solution
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        if (!(str1 + str2).equals(str2 + str1)) {
            return "";
        }
        int len1 = str1.length();
        int len2 = str2.length();
        int gcd = gcd(len1, len2);
        return str1.substring(0, gcd);
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
```javascript []
// javascript solution
/**
 * @param {string} str1
 * @param {string} str2
 * @return {string}
 */
var gcdOfStrings = function(str1, str2) {
    if((str1 + str2) !== (str2 + str1)) return "";
    let len1 = str1.length;
    let len2 = str2.length;


    let val = gcd(len1,len2);
    return str1.substring(0,val);
};
const gcd = (a,b) => {
    while(b!=0){
        let temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
```

## Complexity Analysis 📊

- **Time Complexity:** `O(n + m)`, where `n` and `m` are the lengths of `str1` and `str2`, respectively. The concatenation check takes `O(n + m)` time, and the GCD calculation takes `O(log(min(n, m)))` time.
  
- **Space Complexity:** `O(n + m)` for the concatenated strings used in the check.

---

## Contributing 🙌

Feel free to fork the repository, submit pull requests, or report issues. Contributions are always welcome!

---

## Contact 📧

For any questions or comments, please contact me at [subhadip.it.aec@gmail.com](subhadip.it.aec@gmail.com).

---

**Happy Coding!** 🎉

---
