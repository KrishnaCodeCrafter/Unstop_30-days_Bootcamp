## Problem Statement

A group of explorers stumbles upon an ancient code that could lead them to hidden treasure. The code consists of a number N, and they must figure out all possible pairs of numbers X and Y such that X raised to the power of Y equals N. Help the explorers solve this puzzle by finding all such pairs where X^Y = N, and uncover the treasure's secret!

## Input Format

- The first and only line of input contains a single integer N.

## Output Format

- Print the count of valid pairs on the first line.

- Then, print each pair of X and Y (in ascending order of X) on a new line.

---

## Constraints

- **1 <= N <= 10<sup>6</sup>**

---

## Sample Testcase 0

**Input:**
```bash
16
```

**Output:**
```bash 
3
2 4
4 2
16 1
```

### Explanation


For N=16
16 can be rtepresented as; 2^4 ; 4^2 ; 16^1

## Sample Testcase 1

**Input:**
```bash
23
```

**Output:**
```bash
1
23 1
```
### Explanation

23 can only be represented as 23^1.


---

## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;
vector<pair<int, int>> x_power_y_pairs(int n) {
    vector<pair<int,int>> res;
    for (int y = 2; y <= log(n) / log(2); y++) {
        int x = round(pow(n, 1.0 / y));
        if (pow(x, y) == n) {
            res.push_back({x, y});
        }
    }
    res.push_back({n, 1});
    sort(res.begin(), res.end());
    return res;
}

int main() {
    int n;
    cin >> n;
    
    // Call the user logic function
    vector<pair<int, int>> pairs = x_power_y_pairs(n);
    
    // Output the count of valid pairs
    cout << pairs.size() << endl;
    
    // Output each pair
    for (const auto& pair : pairs) {
        cout << pair.first << " " << pair.second << endl;
    }
    
    return 0;
}
```


Happy coding! 🚀
