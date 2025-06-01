## Problem Statement

A matrix diagonal is a diagonal line of cells starting from some cell in either the topmost row or leftmost column and going in the bottom-right direction until reaching the matrix's end.

For example, the matrix diagonal starting from mat[2][0], where mat is a 6 x 3 matrix, includes cells mat[2][0], mat[3][1], and mat[4][2].

Given an m x n matrix mat of integers, sort each matrix diagonal in ascending order and return the resulting matrix.

## Input Format
 
- The first line contains two space-seperated integers, M and N, representing the number of rows and columns in the matrix.

- The next M lines each contain N space-seperated  integers, representing the elements of the matrix mat.Each line corresponds to a row in the matrix.

## Output Format

- Print the Diagonally sorted matrix. Each row of the matrix should be printed on a new line, as space-seperated integers.



---

## Constraints
- **1 ≤ M,N ≤ 10<sup>2</sup>**  
- **1 ≤ mat[i][j] ≤ 10<sup>2</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
3 4
3 3 1 1
2 2 1 2
1 1 2 2
```

**Output:**
```bash
2 1 1 1
1 2 2 2
1 2 3 3
```

### Explanation

Step-by-Step Sorting:


Diagonal starting at mat[0][0]: [3, 2, 2] → Sorted: [2, 2, 3]<br>
Diagonal starting at mat[0][1]: [3, 1] → Sorted: [1, 3]<br>
Diagonal starting at mat[0][2]: [1] → Sorted: [1]<br>
Diagonal starting at mat[1][0]: [2, 1] → Sorted: [1, 2]<br>
Diagonal starting at mat[2][0]: [1] → Sorted: [1]

## Sample Testcase 1

**Input:**
```bash
3 3
3 1 1
2 5 2
4 2 2
```

**Output:**
```bash
2 1 1
2 3 2
4 2 5
```

### Explanation

Step-by-Step Sorting:


Diagonal starting at mat[0][0]: [3, 5, 2] → Sorted: [2, 3, 5]<br>
Diagonal starting at mat[0][1]: [1, 2] → Sorted: [1, 2]<br>
Diagonal starting at mat[0][2]: [1] → Sorted: [1]<br>
Diagonal starting at mat[1][0]: [2, 2] → Sorted: [2, 2]<br>
Diagonal starting at mat[2][0]: [4] → Sorted: [4]

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

void diagonal_sort(vector<vector<int>>& mat) {
    unordered_map<int,vector<int>> umap;
    int n = mat.size();
    int m = mat[0].size();
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            umap[i-j].push_back(mat[i][j]);
        }
    }
    for(auto &x:umap){
        sort(x.second.rbegin(),x.second.rend());
    }
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            mat[i][j] = umap[i-j].back();
            umap[i-j].pop_back();
        }
    }

}

int main() {
    int m, n;
    cin >> m >> n;
    vector<vector<int>> mat(m, vector<int>(n));
    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            cin >> mat[i][j];
        }
    }

    // Call user logic function
    diagonal_sort(mat);

    // Print the sorted matrix
    for (const auto& row : mat) {
        for (const auto& element : row) {
            cout << element << " ";
        }
        cout << endl;
    }

    return 0;
}

```


Happy coding! 🚀
