# [1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/solutions/5136798/easy-solution-with-explanation-100-runtime-o-n/)

You are given two strings word1 and word2. Merge the strings by adding letters in alternating order,
starting with word1. If a string is longer than the other, append the additional letters onto the end 
of the merged string.

Return the merged string.

## Example 1:
```
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
```

## Example 2:
```
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s
```

## Example 3:
```
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d
```
## Constraints:
- 1 ≤ word1.length, word2.length ≤ 100
- word1 and word2 consist of lowercase English letters.



# Intuition
The problem can be solved by merging two strings alternately.

# Approach

The approach used here is to iterate over both input strings simultaneously and append 
characters alternately to a StringBuilder until one of the strings is exhausted. After 
that, if one of the strings is longer than the other, append the remaining characters of
that string to the StringBuilder.

# Complexity
- Time complexity:

The time complexity of this approach is O(n), where n is the length of the shorter string among 
word1 and word2.

- Space complexity:

The space complexity of this approach is O(n), where n is the length of the longer string among 
word1 and word2.

# Code
```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        StringBuilder sb = new StringBuilder();
        int n = Math.min(word1.length(), word2.length());
        int start = 0;
        while (start < n) {
            sb.append(word1.charAt(start));
            sb.append(word2.charAt(start));
            start++;
        }
        if (word1.length() > start) {
            sb.append(word1.substring(start));
        } else {
            sb.append(word2.substring(start));
        }
        return sb.toString();
    }
}
```

# Discussion
The provided code efficiently merges two strings alternately. It iterates over both strings 
simultaneously and appends characters one by one to the StringBuilder. This approach ensures
optimal time and space complexity.

# Dry Run

For example, let's dry run the input "abc" and "xyz":

- Iteration 1: Append 'a' from word1 and 'x' from word2.
- Iteration 2: Append 'b' from word1 and 'y' from word2.
- Iteration 3: Append 'c' from word1 and 'z' from word2.
- Since both strings are of equal length, the loop stops.
- The final merged string is "axbycz".

` Follow for more contents ` [Github ](https://github.com/subhadip-hazra)
