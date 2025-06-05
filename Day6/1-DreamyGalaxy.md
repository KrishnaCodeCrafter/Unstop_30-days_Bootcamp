## Problem Statement

There are N suns in a galaxy, each sun has M planets, each of the M planets have some number of moons, denoted by galaxy(i)(j), where galaxy(i)(j) denotes the number of moons of the jth planet having the ith sun.

Your task is to determine the maximum number of moons in any solar system. For each sun, calculate the total number of moons across all its planets, and output the highest total number of moons found in a single solar system.

## Input Format
 
- The first line of input contains two space-separated integers, N and M, representing the number of suns and the number of planets per sun, respectively.

- The next N lines of input contains M space separated integers, representing the number of moons for each planet around the respective sun.

## Output Format

- Display a  single integer denoting the maximum total number of moons in a solar system (i.e., across all planets orbiting the same sun).

---

## Constraints
- **1 ≤ N ≤ 5*10<sup>2</sup>**  
- **1 ≤ M ≤ 5*10<sup>2</sup>**  
- **1 ≤ galaxy[i][j] ≤ 10<sup>4</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
2 3
1 2 3
4 5 6
```

**Output:**
```bash
15
```

### Explanation

The second sun has 3 planets and the total of their moons is 15.

## Sample Testcase 1

**Input:**
```bash
1 1
5
```

**Output:**
```bash
5
```

### Explanation

There is only 1 sun and 1 planet having 5 moons.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int calculate_max_moons(int n, int m, const vector<vector<int>>& moons) {
    int ans = 0;
    for(int i=0;i<n;i++){
        int sum = 0;
        for(int j=0;j<m;j++){
            sum += moons[i][j];
        }
        ans = max(ans,sum);
    }

    return ans; // Placeholder return value
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<int>> moons(n, vector<int>(m));
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> moons[i][j];
        }
    }
    
    int result = calculate_max_moons(n, m, moons);
    cout << result << endl;
    return 0;
}


```


Happy coding! 🚀
