## Problem Statement

In a village nestled at the foot of a mountain, skilled artisans crafted magical lanterns that glowed brighter the higher they were carried. To create the most powerful lantern, the village elder needed to calculate its "wish value (absolute difference between maximum and minimum brightness)" by comparing two factors for each mountain peak:

- The maximum brightness from the current peak to the highest point.
- The minimum brightness from the start to that peak.

The elder had to calculate the sum of these wish values to determine the lantern's power. The village eagerly awaited to see if the elder could craft the most powerful lantern ever made.

## Input Format

- The first line contains an integer N, representing the number of mountain peaks.

- The second line contains N space-separated integers A[i], representing the brightness values of each peak.

## Output Format

- Print a single integer representing the sum of all wish values.

---

## Constraints
- **1 ≤ N ≤ 10<sup>6</sup>**  
- **1 ≤ A[i] ≤ 10<sup>6</sup>**  
---

## Sample Testcase 0

**Input:**
```bash
3 
1 2 3
```

**Output:**
```bash
5
```

### Explanation

For each peak:


Peak 0: The maximum brightness from peak 0 to 2 is 3, and the minimum brightness from peak 0 to 0 is 1. Wish value = |3 - 1| = 2


Peak 1: The maximum brightness from peak 1 to 2 is 3, and the minimum brightness from peak 0 to 1 is 1. Wish value = |3 - 1| = 2


Peak 2: The maximum brightness from peak 2 to 2 is 2, and the minimum brightness from peak 0 to 2 is 1. Wish value = |2 - 1| = 1


Sum of all wish values = 2 + 2 + 1 = 5.

## Sample Testcase 1

**Input:**
```bash
5
4 2 3 1 5
```

**Output:**
```bash
15
```

### Explanation

For each peak:


Peak 0: The maximum brightness from peak 0 to 4 is 5, and the minimum brightness from peak 0 to 0 is 4. Wish value = |5 - 4| = 1


Peak 1: The maximum brightness from peak 1 to 4 is 5, and the minimum brightness from peak 0 to 1 is 2. Wish value = |5 - 2| = 3


Peak 2: The maximum brightness from peak 2 to 4 is 5, and the minimum brightness from peak 0 to 2 is 2. Wish value = |5 - 2| = 3


Peak 3: The maximum brightness from peak 3 to 4 is 5, and the minimum brightness from peak 0 to 3 is 1. Wish value = |5 - 1| = 4


Peak 4: The maximum brightness from peak 4 to 4 is 5, and the minimum brightness from peak 0 to 4 is 1. Wish value = |5 - 1| = 4


Sum of all wish values = 1 + 3 + 3 + 4 + 4 = 15

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;


int calculate_wish_values_sum(int n, const vector<int>& arr) {
    vector<int> rmax(n,0);
    rmax[n-1] = arr[n-1];
    for(int i=n-2;i>=0;i--){
        rmax[i] = max(rmax[i+1],arr[i]);
    }
    int res = 0;
    int lmin = INT_MAX;
    for(int i=0;i<n;i++){
        lmin = min(lmin,arr[i]);
        res += (rmax[i] - lmin);
    }
    return res;
}


int main() {
    int N;
    cin >> N;
    vector<int> A(N);
    for (int i = 0; i < N; ++i) {
        cin >> A[i];
    }
    int result = calculate_wish_values_sum(N, A);
    cout << result << endl;
    return 0;
}

```


Happy coding! 🚀
