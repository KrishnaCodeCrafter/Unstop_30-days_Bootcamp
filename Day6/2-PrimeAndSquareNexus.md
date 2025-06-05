## Problem Statement

In a kingdom ruled by numbers, a matrix of size N×N represented the heart of the land. The matrix, filled with positive integers, had special rules:

- Prime Numbers: These guardians of wisdom were replaced by 0 but left no trace in their rows or columns.

- Perfect Squares: These symbols of balance had the power to mark their entire row and column with -1.

The kingdom's rulers needed to organize the matrix by applying these transformations and count:

- The number of rows fully transformed to -1.
- The number of prime numbers replaced with 0.

After processing the matrix, the rulers sought to present the transformed matrix and showcase the results of this magical process.

Note: -1 will have high priority than 0.

## Input Format
 
- The first line contains a single integer N, the size of the matrix.

- The next N lines contain N integers each, representing the elements of the matrix.

## Output Format

- Print two integers: the count of rows fully marked as -1 and the count of prime numbers replaced with 0.

- Print the modified matrix with elements of the same row separated by a single space. Start the next row on a new line.

---

## Constraints
- **2 ≤ N ≤ 100**  
- **1 ≤ grid[i][j] ≤ 10<sup>6</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
4
2 6 4 8
5 9 12 15
10 11 18 7
20 21 25 16
```

**Output:**
```bash
3 0
-1 -1 -1 -1
-1 -1 -1 -1
10 -1 -1 -1
-1 -1 -1 -1
```

### Explanation

In the given matrix,<br>
The element 2, 5, 11, 7 are prime so replace them with 0.<br>
0 6 4 8<br>
0 9 12 15<br>
10 0 18 0<br>
20 21 25 16

Now, 4, 9, 25 and 16 are perfect square, so replace the entire row and column with -1.<br>
-1 -1 -1 -1<br>
-1 -1 -1 -1<br>
10 -1 -1 -1<br>
-1 -1 -1 -1<br>
Since -1 have high priority than 0, so it has replace all 0s.<br>
Number of rows entirely marked as -1 = 3<br>
Number of zeroes : 0 (we have to considered the final matrix after replacements)

## Sample Testcase 1

**Input:**
```bash
3
4 5 6
2 11 13
12 18 10
```

**Output:**
```bash
1 2
-1 -1 -1
-1 0 0
-1 18 10
```

### Explanation

In the given matrix,<br>
The element 2, 5, 11 and 13 are prime so replace them with 0.<br>
4 0 6<br>
0 0 0<br>
12 18 10<br>

Now, 4 is a perfect square, so replace the entire row and column with -1.<br>
-1 -1 -1<br>
-1 0 0<br>
-1 18 10<br>

Since -1 have high priority than 0, so it has replace the 0s present in (0,1) and (1,0).<br>
Number of rows entirely marked as -1 = 1<br>
Number of zeroes : 2 (we have to considered the final matrix after replacements)

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

bool isPerfectSquare(int x){
    int root = sqrt(x);
    int y = root*root;
    return (y == x); 
}

bool isPrime(int num){
    if(num <= 1)
        return false;
    int limit = sqrt(num);
    for(int i=2;i<=limit;i++){
        if(num%i == 0)
            return false;
    }
    return true;
}

void transform_matrix(vector<vector<int>>& matrix, int n, int& row_count, int& prime_count) {
    vector<bool> row(n,false);
    vector<bool> col(n,false);
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(isPerfectSquare(matrix[i][j])){
                row[i] = true;
                col[j] = true;
            }
        }
    }

    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(row[i] || col[j]){
                matrix[i][j] = -1;
            }else if(isPrime(matrix[i][j])){
                prime_count++;
                matrix[i][j] = 0;
            }
        }
    }

    for(auto x:row){
        if(x)
            row_count++;
    }

}

int main() {
    int n;
    cin >> n;
    vector<vector<int>> matrix(n, vector<int>(n));
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < n; ++j) {
            cin >> matrix[i][j];
        }
    }

    int row_count = 0;
    int prime_count = 0;
    transform_matrix(matrix, n, row_count, prime_count);

    cout << row_count << " " << prime_count << endl;
    for (const auto& row : matrix) {
        for (int val : row) {
            cout << val << " ";
        }
        cout << endl;
    }

    return 0;
}

```


Happy coding! 🚀
