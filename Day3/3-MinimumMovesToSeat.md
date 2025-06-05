## Problem Statement

Pavel is given a room with N seats and N students.

- Each seat's position is represented by the array seats of length N, where seats[i] indicates the position of the ith seat.
- Similarly, the positions of the students are given in an array students of length N, where students[j] represents the position of the jth student.

Pavel is allowed to move each student by one position to the left or right any number of time. The goal is to find the minimum number of moves required to shift the students to seats in such a way that no two students are seated together.

## Input Format

- The first line of the input contains an integer N representing the number of seats and students.

- The second line contains N space-separated integers representing the position of ith seats.

- The third line contains N space-separated integers representing the position of ith students.

## Output Format

- Print the minimum number of moves required to move each student to a seat.

---

## Constraints
- **N == seats.length == students.length**  
- **1 ≤ N ≤ 100**  
- **1 <= seats[i], students[j] <= 100**  
---

## Sample Testcase 0

**Input:**
```bash
4
2 4 6 8
2 4 6 8
```

**Output:**
```bash
0
```

### Explanation

Similar to the previous case, the initial arrangement already satisfies the condition. No moves are necessary.

## Sample Testcase 1

**Input:**
```bash
5
1 3 5 7 9
2 4 6 8 10
```

**Output:**
```bash
5
```

### Explanation

The students start at positions [2, 4, 6, 8, 10], but they need to be moved to [1, 3, 5, 7, 9] to ensure that no two students are adjacent.


The minimum moves required:<br>
Move student from 2 → 1 (1 move)<br>
Move student from 4 → 3 (1 move)<br>
Move student from 6 → 5 (1 move)<br>
Move student from 8 → 7 (1 move)<br>
Move student from 10 → 9 (1 move)<br>
Total moves = 5

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int calculate_min_moves(vector<int>& seats, vector<int>& students) {
    int n = seats.size();
    sort(seats.begin(),seats.end());
    sort(students.begin(),students.end());
    int res = 0;
    for(int i=0;i<n;i++){
        res += abs(students[i] - seats[i]);
    } 

    return res;
}

int main() {
    int n;
    cin >> n;
    vector<int> seats(n);
    vector<int> students(n);
    for (int i = 0; i < n; ++i) {
        cin >> seats[i];
    }
    for (int i = 0; i < n; ++i) {
        cin >> students[i];
    }
    int result = calculate_min_moves(seats, students);
    cout << result << endl;
    return 0;
}

```


Happy coding! 🚀
