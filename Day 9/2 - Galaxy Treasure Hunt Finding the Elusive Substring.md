## Problem Statement

In a distant galaxy, a young inventor named Leo created a robot called "Trace" to help him find hidden treasures. These treasures were marked on ancient maps stored as long strings of mysterious text. To locate a treasure, Trace needed to find a specific clue called the Key, made up of a unique combination of characters.

The maps were massive and full of random symbols, making Trace’s task difficult. The Key could appear in any part of the map, but its characters might be jumbled. Trace’s job was to find the shortest section(substring) of the map that included all the characters of the Key, no matter the order.  If no such substring exists, Trace should return -1.

## Input Format

- The first line contains a string S representing the map.

- The second line contains a string T representing the Key.

## Output Format

- Output the length of the shortest substring of s that contains all the characters of t in any order. If no such substring exists, output -1.

---

## Constraints

- **Each character of S and T is a printable ASCII character.**
- **1 ≤ |S| ≤ |T| ≤ 10<sup>5</sup>**

---

## Sample Testcase 0

**Input:**
```bash
warrmioruhk
warrior
```

**Output:**
```bash
8
```

### Explanation

The shortest substring of S that contains all the characters of T is "warrmior", which has length 8.

## Sample Testcase 1

**Input:**
```bash
Thunder
King
```

**Output:**
```bash
-1
```

### Explanation

There is no substring of S that contains all the characters of T.

---

## Solution (C++)

```cpp


```


Happy coding! 🚀
