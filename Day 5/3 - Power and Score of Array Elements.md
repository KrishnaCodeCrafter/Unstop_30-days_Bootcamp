## Problem Statement

Given an array arr[] (0-based indexed) of integers of size N, define the power of the integer at index i as follows:

Let:

- a be the second minimum integer among all integers with indices less than i .
- b be the second minimum integer among all integers with indices greater than i.

The power of the integer at index i is defined as:
max(arr[i] - a, arr[i] - b).

The score of the array arr is defined as the sum of powers for all integers in the array. Print the score of the array arr.

Note: If there are less than equal to one element before or after the index i, then consider the second minimus as INT_MAX.

## Input Format
 
- The first line contains an integer N which denotes the size of the array.

- The second line contains N space-separated integers denoting the elements of the array arr[].

## Output Format

- Print an integer denoting the score of the array.

---

## Constraints
- **K ≤ N ≤ 10<sup>5</sup>**  
- **1 ≤ Arr[i] ≤ 10<sup>6</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
5
4 7 1 8 3
```

**Output:**
```bash
2
```

### Explanation

Index 0 (arr[0] = 4):<br>
Before: INT_MAX (no elements).<br>
After: Second minimum in [7, 1, 8, 3] = 3.<br>
Score: max(4 - INT_MAX, 4 - 3) = 1.

Index 1 (arr[1] = 7):<br>
Before: Second minimum in [4] = INT_MAX.<br>
After: Second minimum in [1, 8, 3] = 3.<br>
Score: max(7 - INT_MAX, 7 - 3) = 4.


Index 2 (arr[2] = 1):<br>
Before: Second minimum in [4, 7] = 7.<br>
After: Second minimum in [8, 3] = 8.<br>
Score: max(1 - 7, 1 - 8) = -6.


Index 3 (arr[3] = 8):<br>
Before: Second minimum in [4, 7, 1] = 4.<br>
After: INT_MAX (no elements).<br>
Score: max(8 - 4, 8 - INT_MAX) = 4.


Index 4 (arr[4] = 3):<br>
Before: Second minimum in [4, 7, 1, 8] = 4.<br>
After: INT_MAX (no elements).<br>
Score: max(3 - 4, 3 - INT_MAX) = -1.


Total Score: 1 + 4 - 6 + 4 - 1 = 2.

## Sample Testcase 1

**Input:**
```bash
4
3 8 1 6
```

**Output:**
```bash
-5
```

### Explanation

Index 0 (arr[0] = 3):<br>
Before: INT_MAX (no elements).<br>
After: Second minimum in [8, 1, 6] = 6.<br>
Score: max(3 - INT_MAX, 3 - 6) = -3.


Index 1 (arr[1] = 8):<br>
Before: Second minimum in [3] = INT_MAX.<br>
After: Second minimum in [1, 6] = 6.<br>
Score: max(8 - INT_MAX, 8 - 6) = 2.


Index 2 (arr[2] = 1):<br>
Before: Second minimum in [3, 8] = 8.<br>
After: Second minimum in [6] = INT_MAX.<br>
Score: max(1 - 8, 1 - INT_MAX) = -7.


Index 3 (arr[3] = 6):<br>
Before: Second minimum in [3, 8, 1] = 3.<br>
After: INT_MAX (no elements).<br>
Score: max(6 - 3, 6 - INT_MAX) = 3.


Total Score: -3 + 2 - 7 + 3 = -5.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int computeScore(vector<int>& arr) {
    int n = arr.size();
    vector<long long> prefix(n,INT_MAX);
    vector<long long> suffix(n,INT_MAX);
    if(n > 2){
        //Prefix
        long long premini1 = min(arr[0],arr[1]);
        long long premini2 = max(arr[0],arr[1]);
        for(int i=2;i<n;i++){
            prefix[i] = premini2;
            if(arr[i] < premini1){
                premini2 = premini1;
                premini1 = arr[i];
            }else if(arr[i] < premini2 && arr[i] != premini1){
                premini2 = arr[i];
            }
        }

        //Suffix
        long long suffmini1 = min(arr[n-1],arr[n-2]);
        long long suffmini2 = max(arr[n-1],arr[n-2]);
        for(int i=n-3;i>=0;i--){
            suffix[i] = suffmini2;
            if(arr[i] < suffmini1){
                suffmini2 = suffmini1;
                suffmini1 = arr[i];
            }else if(arr[i] < suffmini2 && arr[i] != suffmini1){
                suffmini2 = arr[i];
            }
        }
    }

    int result = 0;
    for(int i=0;i<n;i++){
        result += max(arr[i]-prefix[i] , arr[i]-suffix[i]);
    }
    return result;
}

int main() {
    int n;
    cin >> n; // First input is the integer n
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) {
        cin >> arr[i]; // Remaining input is the array of integers
    }

    // Call user logic function and print the output
    int result = computeScore(arr);
    cout << result << endl;
    return 0;
}

```


Happy coding! 🚀
