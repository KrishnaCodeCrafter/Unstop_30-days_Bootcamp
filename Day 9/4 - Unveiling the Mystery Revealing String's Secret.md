## Problem Statement

Once upon a time, in a small village, there were two friends named Alice and Bob. They loved solving puzzles together. One day, Alice gave Bob a special task to help her solve a mystery involving strings.

Alice had a string T, a secret message, and Bob had a string S, which was a sequence of random letters. Bob had an interesting habit — every day, he would reverse the string he had and then append the original string S to the reversed string. Alice was curious to know on which day the secret message T would first appear as a subsequence in Bob's growing string.

For example, if S was “abc”, Bob would start with “abc” on the first day. The next day, he would reverse “abc” to get “cba” and append “abc” again, so his string would become “cbaabc”. On the third day, Bob would reverse “cbaabc” to get “cbacba” and then append “abc” again, resulting in “cbacbaabc”.

Alice, being a curious mind, wanted to know the first day on which her secret message T would show up as a subsequence in Bob’s string. Bob kept repeating his string-reversing and appending process every day, but Alice couldn’t keep track of when exactly her message would appear.

## Input Format

- The first line of the input contains Bob's string S.

- The second line of the input contains Alice's string T.



## Output Format

- Output a single integer, representing the number of days when Alice's string will be a subsequence of Bob's string for the first time.

---

## Constraints

- **1 <= |S| and |T| <= 10<sup>3</sup>**

- **String T contain characters that are present in S.**

---

## Sample Testcase 0

**Input:**
```bash
abcd
cba
```

**Output:**
```bash
2
```

### Explanation

Day 1: The string Bob has is "abcd". We check if "cba" is a subsequence of "abcd". It’s not, because the characters "cba" do not appear in that order. So, on Day 1, "cba" is not a subsequence.


Day 2: Bob reverses "abcd" to "dcba" and appends S, forming "dcbaabcd". We check if "cba" is a subsequence of "dcbaabcd". It’s still not, because the order "cba" does appear in the string. So, on Day 2, "cba" is a subsequence.

## Sample Testcase 1

**Input:**
```bash
jabgi
gij
```

**Output:**
```bash
3
```

### Explanation

Day 1: The string Bob has is S = "jabgi". We check if "gij" is a subsequence of "jabgi". It’s not, because we cannot find "gij" in that order.


Day 2: Bob reverses "jabgi", which becomes "igbaj", and appends S again, forming "igbajjabgi". We check if "gij" is a subsequence of "igbajjabgi". This still isn’t true.

---

## Solution (C++)

```cpp


```


Happy coding! 🚀
