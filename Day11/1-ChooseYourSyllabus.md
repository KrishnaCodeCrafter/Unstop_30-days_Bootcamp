## Problem Statement

In a classroom debate, two syllabuses—Syllabus 1 and Syllabus 2—are being compared to determine which one is more engaging for students. Each syllabus contains an equal number of chapters. The syllabus with the higher interest value is selected for teaching.

Interest Value Calculation<br>
The interest value of a syllabus is defined as the sum of the intent values of all its chapters.

The intent value of a chapter is determined as follows:

- For a given chapter in one syllabus, count the number of chapters in the other syllabus that have an intrinsic value less than or equal to its own intrinsic value.
- The sum of these counts across all chapters gives the total interest value of the syllabus.

The syllabus with the higher interest value is chosen.

## Input Format

- The first line contains n, the number of chapters in both syllabuses.

- The second line contains n numbers, ai, the intrinsic values for all the chapters in syllabus 1.

- The third line contains n numbers, bi, the intrinsic values for all the chapters in syllabus 2

## Output Format

- Your task is to print the highest interest value among both available syllabuses.

---

## Constraints

- **1<=n<=10<sup>5</sup>**

- **1<=ai<=10<sup>9</sup>**

- **1<=bi<=10<sup>9</sup>**

---

## Sample Testcase 0

**Input:**
```bash
1
2
4
```

**Output:**
```bash
1
```

### Explanation

Syllabus 1: [2]<br>
Intent value for chapter 2: 0 (since no chapters in Syllabus 2 have intrinsic values ≤ 2).<br>
Total interest value of Syllabus 1 = 0.


Syllabus 2: [4]<br>
Intent value for chapter 4: 1 (since one chapter in Syllabus 1 has an intrinsic value ≤ 4).<br>
Total interest value of Syllabus 2 = 1.


The highest interest value is 1.

## Sample Testcase 1

**Input:**
```bash
5
1 2 6 3 2 
2 4 1 12 2
```

**Output:**
```bash
16
```

### Explanation

Intrinsic values for each syllabus:<br>
Syllabus 1: [1, 2, 6, 3, 2]<br>
Syllabus 2: [2, 4, 1, 12, 2]


Calculating interest values:<br>
Syllabus 1:<br>
Chapter 1 (1): Count of values in Syllabus 2 ≤ 1 → 1<br>
Chapter 2 (2): Count of values in Syllabus 2 ≤ 2 → 3<br>
Chapter 3 (6): Count of values in Syllabus 2 ≤ 6 → 4<br>
Chapter 4 (3): Count of values in Syllabus 2 ≤ 3 → 3<br>
Chapter 5 (2): Count of values in Syllabus 2 ≤ 2 → 3<br>
Total interest value of Syllabus 1 = 1 + 3 + 4 + 3 + 3 = 14


Syllabus 2:<br>
Chapter 1 (2): Count of values in Syllabus 1 ≤ 2 → 3<br>
Chapter 2 (4): Count of values in Syllabus 1 ≤ 4 → 4<br>
Chapter 3 (1): Count of values in Syllabus 1 ≤ 1 → 1<br>
Chapter 4 (12): Count of values in Syllabus 1 ≤ 12 → 5<br>
Chapter 5 (2): Count of values in Syllabus 1 ≤ 2 → 4<br>
Total interest value of Syllabus 2 = 3 + 4 + 1 + 5 + 4 = 16

The highest interest value is 16.



---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int solve(vector<int>& a,vector<int>& b){
    int n = a.size();
    int cnt = 0;
    for(int i=0;i<n;i++){
        int num = a[i];
        cnt += (upper_bound(b.begin(),b.end(),num) - b.begin());
    }
    return cnt;
}

int user_logic(int n, vector<int>& a, vector<int>& b) {
    sort(a.begin(),a.end());
    sort(b.begin(),b.end());
    
    int cnt1 = solve(a,b);
    int cnt2 = solve(b,a);

    return max(cnt1,cnt2);
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n), b(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    for (int i = 0; i < n; i++) {
        cin >> b[i];
    }
    int result = user_logic(n, arr, b);
    cout << result << endl;
    return 0;
}


```


Happy coding! 🚀
