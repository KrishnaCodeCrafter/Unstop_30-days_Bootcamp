## Problem Statement

In an assembly line at St. Mary School, N students stand in ascending order of their heights. Nidhi Sharma, a teacher, has k queries where she asks about the height H of a particular student. The task is to determine the position (0-based index) of the student in the line if they are present. If the student is absent, the task is to find the correct position where that student should be placed to maintain the ascending order.

## Input Format

- The first line contains the integer N denoting the total no. of students.

- The second line contains N space-separated integers representing the height of students standing in a line.

- The third line contains an integer k denoting the number of queries of the teacher.

- Next k lines contain a single integer on each line denoting the height of the student H that is enquired.

## Output Format

- For each query, output the proper position (0-based index) of the student in a new line.

---

## Constraints

- **1<=k<=10<sup>3</sup>**
- **1<=N<=10<sup>8</sup>**
- **1<=hi<=10<sup>4</sup>**
- **1<=H<=10<sup>4</sup>**

---

## Sample Testcase 0

**Input:**
```bash
5
12 34 45 89 110
5
23
45
11
90
150
```

**Output:**
```bash
1
2
0
4
5
```

### Explanation

23: The height 23 is not present in the list, but it should be placed between 12 and 34 to maintain ascending order. So, its correct position (0-based index) is 1.

45: The height 45 is present in the list at position 2 (0-based index), so the correct position (0-based index) is 2.

11: The height 11 is not present, and it would be placed before 12. So, its correct position (0-based index) is 0.

90: The height 90 is not present, but it should be placed after 89 and before 110. So, its correct position (0-based index) is 4.

150: The height 150 is not present and would be placed after 110. So, its correct position (0-based index) is 5.

## Sample Testcase 1

**Input:**
```bash
4
1 3 5 6
2
5
7
```

**Output:**
```bash
2
4
```

### Explanation

The first query asks for the position of the student with a height 5. Since 5 is present in the list at position 2 (0-based index).

The second query asks for the position of the student with height 7. Since 7 is not present, but it would be placed after 6 to maintain ascending order, its correct position (0-based index) is 4.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

void find_student_positions(int n, vector<int>& heights, int k, vector<int>& queries, vector<int>& results) {
    for(int i=0;i<queries.size();i++){
        int x = queries[i];
        int low = 0;
        int high = n-1;
        while(low <= high){
            int mid = low + (high - low)/2;
            if(heights[mid] >= x){
                high = mid-1;
            }else
                low = mid+1;
        }
        results[i] = low;
    }
}

int main() {
    int n, k;
    cin >> n;
    vector<int> heights(n);
    for (int i = 0; i < n; ++i) {
        cin >> heights[i];
    }
    cin >> k;
    vector<int> queries(k);
    for (int i = 0; i < k; ++i) {
        cin >> queries[i];
    }
    vector<int> results(k);
    find_student_positions(n, heights, k, queries, results);
    for (int i = 0; i < k; ++i) {
        cout << results[i] << endl;
    }
    return 0;
}

```


Happy coding! 🚀
