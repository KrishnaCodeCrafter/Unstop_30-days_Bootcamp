## Problem Statement

In a futuristic space station, a garden of genetically engineered plants generates energy pods, represented as an array E of size N, where E[i] is the number of energy pods produced by the i-th plant. Commander Zeta must divide the garden into three continuous zones: Alpha, Beta and Gamma where the zone size of alpha must be same as the zone size of gamma.

- Alpha and Gamma for the Energy Council, and Beta for the Defense Alliance. Since Zone Beta is inefficient and wastes energy, Zeta decides to ensure its energy is always less than the combined energy of Zones Alpha and Gamma.

Determine the total number of ways this division can be accomplished while adhering to this condition.

## Input Format
 
- The first line contains an integer N representing the number of plants.

- The second line contains N space separated integers, where the i-th integer represents the energy pods produced by the i-th plant.

## Output Format

- Print a single integer representing the total number of ways to divide the garden into the three zones such that the sum of energy pods in Alpha and Gamma combined is greater than the energy pods in Beta.

---

## Constraints
- **1 ≤ N ≤ 10<sup>5</sup>**  
- **1 ≤ E[i] ≤ 10<sup>5</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
4
3 3 3 3
```

**Output:**
```bash
0
```

### Explanation

For the array [3, 3, 3, 3], there are no valid divisions possible.

## Sample Testcase 1

**Input:**
```bash
5
1 2 3 4 5
```

**Output:**
```bash
1
```

### Explanation

For the array [1, 2, 3, 4, 5], there will be only one possible division.<br>
Alpha: [1, 2], Beta: [3], Gamma: [4, 5] → (3 + 9 > 3)

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int countValidPartitions(vector<int>& arr, int n) {
    long beta = 0;
    for(int i=0;i<n;i++){
        beta += arr[i];
    }

    long ans = 0;
    int l = 0;int r = n-1;
    long alpha = 0;long gamma = 0;
    for(int i=0;i<=(n-1)/2;i++){
        if(alpha+gamma > beta){
            ans++;
        }
        alpha += arr[l];
        gamma += arr[r];
        beta -= arr[l];beta -= arr[r];
        l++;r--;
    }

    return ans; // Placeholder return value
}

int main() {
    int N;
    cin >> N; // Read the number of plants

    vector<int> arr(N);
    for (int i = 0; i < N; ++i) {
        cin >> arr[i];
    }

    int result = countValidPartitions(arr, N);

    cout << result << endl;

    return 0;
}



```


Happy coding! 🚀
