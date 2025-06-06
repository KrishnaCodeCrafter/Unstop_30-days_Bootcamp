## Problem Statement

The exam scores for a class of N students have been released. The marks obtained by each student are stored in an array of scores[], where scores[i] represent the marks of the ith student.

As the class monitor, Ram is tasked with answering queries from the teacher. The teacher will ask Q queries, and for each query, Ram needs to determine how many students have scored at least X marks.

Your objective is to help Ram by finding the number of students who have scored at least X marks for each query.

## Input Format

- The first line contains two positive integers N, and Q, denoting the number of students and the number of queries, respectively.

- This is followed by a line containing N integers, separated by space giving the scores of each student.

- Then, Q lines follow where the ith line contains a single integer X.
 

## Output Format

- For each query, print a single integer representing the number of students who scored at least X marks.

---

## Constraints

- **1 <= N, Q <= 2 * 10<sup>5</sup>**
- **1 <= X <= 10<sup>9</sup>**
- **1 <= scores[i] <= 10<sup>9</sup>**

---

## Sample Testcase 0

**Input:**
```bash
5 2
1 4 12 3 9
2
15
```

**Output:**
```bash 
4
0
```

### Explanation

There are 5 students with scores [1, 4, 12, 3, 9].

The first query asks for the number of students who scored at least 2 marks. The students with scores [4, 12, 3, 9] meet this criterion, resulting in 4 students.

The second query asks for the number of students who scored at least 15 marks. No student meets this criterion, resulting in 0 students.<br>
Therefore, the outputs are 4 and 0 respectively.


## Sample Testcase 1

**Input:**
```bash
4 1
2 3 1 4 
3
```

**Output:**
```bash
2
```
### Explanation

There are 4 students with scores [2, 3, 1, 4].<br>
The query asks for the number of students who scored at least 3 marks.<br>
The students with scores of 3 and 4 meet this criterion.<br>
Therefore, the output is 2.

---

## Solution (C++)

```cpp


```


Happy coding! 🚀
