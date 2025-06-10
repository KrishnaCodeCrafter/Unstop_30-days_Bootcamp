## Problem Statement

In a classroom with N students and N available seats, each student has a preferred seat number, given in an array A. Students enter the classroom one by one in order from student 1 to N.

Each student follows these rules when choosing a seat:

- If their preferred seat is vacant, they sit there.
- If their preferred seat is occupied, they continue searching circularly (wrapping around if needed) until they find an empty seat.

Your task is to determine the final seating arrangement of all students.

## Input Format

- The first line contains an integer N (the number of students and seats).

- The second line contains N space-separated integers representing the seat preferences of the students. The seat numbers are typically between 1 and N.

## Output Format

- Print a list of space-seperated integers representing the final seating arrangement, with each student seated in the correct order.


---

## Constraints

- **1 <= N <= 10<sup>5</sup>.**

- **1 <= A[i] <= N.**

---

## Sample Testcase 0

**Input:**
```bash
3 
3 3 3
```

**Output:**
```bash 
3 1 2
```

### Explanation

Initially, all seats are empty: [_, _, _].<br>
Student 1 prefers seat 3, which is available. They take it: [_, _, S1].<br>
Student 2 also prefers seat 3, but it’s occupied. They move circularly and take the next available seat 1: [S2, _, S1].<br>
Student 3 also prefers seat 3, but it’s occupied. They move circularly and take the last available seat 2: [S2, S3, S1].


Final seating arrangement:<br>
S1 takes Seat 3.<br>
S2 takes Seat 1.<br>
S3 takes Seat 2.

## Sample Testcase 1

**Input:**
```bash
1
1
```

**Output:**
```bash
1
```
### Explanation

There is only a single student, so he will get his desired seat.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

void assignSeats(int totalSeats, vector<int>& preferences, vector<int>& seatingArrangement) {
    vector<int> seatTaken(totalSeats, 0);
    for (int i = 0; i < totalSeats; i++) {
        if (seatTaken[preferences[i] - 1] == 0) {
            seatingArrangement[i] = preferences[i];
            seatTaken[preferences[i] - 1] = 1;
        } else {
            int nextSeat = preferences[i] % totalSeats;
            while (seatTaken[nextSeat] != 0) {
                nextSeat++;
                if (nextSeat >= totalSeats) nextSeat = nextSeat % totalSeats;
            }
            seatingArrangement[i] = nextSeat + 1;
            seatTaken[nextSeat] = 1;
        }
    }
}

int main() {
    int n;
    cin >> n;
    vector<int> seat_preferences(n);
    for (int i = 0; i < n; ++i) {
        cin >> seat_preferences[i];
    }
    vector<int> final_seating(n);
    assignSeats(n, seat_preferences, final_seating);
    for (int i = 0; i < n; ++i) {
        cout << final_seating[i] << " ";
    }
    cout << endl;
    return 0;
}


```


Happy coding! 🚀
