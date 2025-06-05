## Problem Statement

Given an array of integers arr[] of size N, find the two smallest integers in the array and form the largest possible number using them. Output this largest number

## Input Format

- The first line contains an integer, where N denotes the number of elements in the array in the array.
- The second line contains N space-separated integers.

## Output Format

- Print the largest number that can be formed.

---

## Constraints
- **1 ≤ N ≤ 10<sup>2</sup>**  
- **0 ≤ arr[i] ≤ 9**  
---

## Sample Testcase 0

**Input:**
```bash
7
1 2 3 4 5 6 7
```

**Output:**
```bash
21
```

### Explanation

The two minimum numbers out of the given array are 1 and 2. If we try to make the largest number possible using these two numbers, we get 21.

## Sample Testcase 1

**Input:**
```bash
4
7 8 9 6
```

**Output:**
```bash
76
```

### Explanation

The two minimum numbers out of the given array are 6 and 7. If we try to make the largest number possible using these two numbers, we get 76.

---

## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;

// Placeholder function for user logic
int findLargestNumber(vector<int>& arr) {
    sort(arr.begin(),arr.end());

    int num = arr[0];
    num += arr[1]*10;
        
    return num; 
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) {
        cin >> arr[i];
    }
    // Call user logic function and print the output
    int result = findLargestNumber(arr);
    cout << result << endl;
    return 0;
}
```


Happy coding! 🚀
