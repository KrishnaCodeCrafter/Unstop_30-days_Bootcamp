## Problem Statement

Given a n * m matrix of ones and zeros, where 0 denotes water and 1 denotes island, now you have to count the total number of square submatrices that consist entirely of 1s. 

## Input Format
 
- First line contains n and m, where n is the number of rows and m is the column.
- From second line it contains the elements of the arr matrix.

## Output Format

- Print the count of the number of square sub-island. 

---

## Constraints
- **1 ≤ arr.length ≤ 300**  
- **1 ≤ arr[0].length ≤ 300**  
- **1 ≤ arr[i][j] ≤ 1**  

---

## Sample Testcase 0

**Input:**
```bash
3 3
1 0 1
1 1 0
1 1 1
```

**Output:**
```bash
8
```

### Explanation

There are 7 squares of side 1.<br>
There are 1 squares of side 2.<br>
There is  0 square of side 3.<br>
Total number of squares = 7 + 1 + 0 = 8.

## Sample Testcase 1

**Input:**
```bash
3 3
1 0 1
1 1 0
1 1 0
```

**Output:**
```bash
7
```

### Explanation

There are 6 squares of side 1.  <br>
There is 1 square of side 2. <br>
Total number of squares = 6 + 1 = 7.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int count_square_sub_islands(const vector<vector<int>>& matrix) {
    int n = matrix.size();
    int m = matrix[0].size();

    vector<vector<int>> dp(n,vector<int>(m,0));

    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            if(i == 0 || j == 0){
                dp[i][j] = matrix[i][j];
            }else{
                dp[i][j] = ((matrix[i][j])?matrix[i][j]+min({dp[i][j-1],dp[i-1][j],dp[i-1][j-1]}):0);
            }
        }
    }
    int total = 0;
    for(auto &x:dp){
        for(auto &y:x){
            total += y;
        }
    }

    return total;
}

int main() {
    int n, m;
    cin >> n >> m;

    vector<vector<int>> matrix(n, vector<int>(m));
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> matrix[i][j];
        }
    }

    int result = count_square_sub_islands(matrix);
    cout << result << endl;

    return 0;
}

```


Happy coding! 🚀
