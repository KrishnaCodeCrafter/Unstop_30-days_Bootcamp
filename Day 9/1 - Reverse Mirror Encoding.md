## Problem Statement

Ram and Shyam have devised a new encoding scheme called "Reverse Mirror Encoding." In this system:

- For letters 'a' to 'n', the code is their reverse position in the first half of the alphabet.

    - Example: 'a' → n, 'b' → m, ..., 'n' →a.
- For letters 'o' to 'z', the code is their reverse position in the second half of the alphabet followed by a #.

    - Example: 'o#' → z, 'p#' → y, ..., y# → p, 'z#' → o.

Given a coded message S, determine the original decoded message Ram sent to Shyam.

## Input Format

- The first and only line of input contains a single string S, representing the encoded message.


## Output Format

- Print a single string, representing the decoded message.


---

## Constraints

- **2 <= |S| <= 10<sup>3</sup>**

---

## Sample Testcase 0

**Input:**
```bash
u#jlg
```

**Output:**
```bash
tech
```

### Explanation

'u#' → 't'.<br>
'j' → 'e'.<br>
'l' → 'c'.<br>
'g' → 'h'.<br>
Decoded message: "tech".

## Sample Testcase 1

**Input:**
```bash
mjt#av#u#z#y#y#nmcj
```

**Output:**
```bash
beunstoppable
```

### Explanation

'm' → 'b'.<br>
'j' → 'e'.<br>
't#' → 'u'.<br>
'a' → 'n'.<br>
'v#' → 's'.<br>
'u#' → 't'.<br>
'z#' → 'o'.<br>
'y#' → 'p'.<br>
'y#' → 'p'.<br>
'n' → 'a'.<br>
'm' → 'b'.<br>
'c' → 'l'.<br>
'j' → 'e'.<br>
Decoded message: "beunstoppable".

---

## Solution (C++)

```cpp


```


Happy coding! 🚀
