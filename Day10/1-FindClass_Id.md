## Problem Statement

In a school the class strength is represented as per following

Eg: if a[2]=20. The number of students in class 2 is 20, here 2 is the class_id.

Your task is to print X, the class_id of the first class with the number of students greater than or equal to the number of students in adjacent previous classes and also greater than or equal to the number of students in the adjacent class after it.

Print the value of X.

Note : - The array is 0 index-based.

## Input Format

- In the first line, you are given an integer, n, denoting the size of the array

- In the second line, you are given n-spaced integers denoting the array.


## Output Format

- An integer value will be displayed representing X.

---

## Constraints

- **3 <= arr.length <= 10<sup>4</sup>**
- **0 <= arr[i] <= 10<sup>6</sup>**
- **arr is guaranteed to be a mountain array.**

---

## Sample Testcase 0

**Input:**
```bash
3
0 1 0
```

**Output:**
```bash
1
```

### Explanation

Since 1 is the maximum value in the given array and its index is 1, so answer comes out to be 1

## Sample Testcase 1

**Input:**
```bash
9
1 2 3 4 5 5 6 7 54
```

**Output:**
```bash
4
```

### Explanation

Here at the class_id the number of students is 5 which is greater than it's previous class_id 3 and equal to the next class_id 5.

---

## Solution (C++)

```cpp


```


Happy coding! 🚀
