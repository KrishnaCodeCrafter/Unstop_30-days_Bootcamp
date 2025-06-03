## Problem Statement

You are an agent, to stop an attack you have to decipher a piece of encrypted code. 

The encrypted code contains two lines each containing a sequence of characters. You know that to decipher the code you have to merge the two lines by adding characters in alternating sequence. Finally, if one sequence is longer than the other append it to the end. 

Help the agent decrypt the code as soon as possible. 

## Input Format

- The first line of the input contains an integer n  — the size of the first sequence.

- The second line of the input contains the first sequence.

- The third line of the input contains an integer m  — the size of the second sequence.

- The fourth line of the input contains the second sequence.

## Output Format

- Print the decoded sequence of characters. 

---

## Constraints

- **1 <= sequence1.length, sequence2.length <= 100**
- **Sequence1 and sequence2 consist of lowercase English letters.**

---

## Sample Testcase 0

**Input:**
```bash
5
bmatc
5
obtak
```

**Output:**
```bash
bombattack
```

### Explanation

Adding each character in the sequence:


From 1 string (0th Character) - From 2nd string(0th Character) - From 1str string(1st Character) - From 2nd String (From 1st Character) - From 1str String.....


b - o - m - b - a - t - t - a - c - k


We get the string as "bombattack"
## Sample Testcase 1

**Input:**
```bash
4
ctho
5
acfur
```

**Output:**
```bash
catchfour
```

### Explanation

Adding each character in the sequence:


From 1 string (0th Character) - From 2nd string(0th Character) - From 1str string(1st Character) - From 2nd String (From 1st Character) - From 1str String.....


c - a - t - c - h - f - o - u + r (remaining characters)

---

## Solution (C++)

```cpp


```


Happy coding! 🚀
