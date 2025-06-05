## Problem Statement

Chris is at the entrance of Adventureland, where there is a magic grid of size N×N, filled entirely with the number 1.

To gain entry, he must quickly calculate the sum of the integers on both the main and secondary diagonals of the grid.

The main diagonal consists of elements where the row and column indices are the same, i.e., (0,0), (1,1), (2,2), ..., (N-1,N-1).

The secondary diagonal consists of elements where the row index and column index sum to N−1, i.e., (0,N-1), (1,N-2), (2,N-3), ..., (N-1,0).

Note: If N is odd, the center element (at index (N//2,N//2)) is counted twice, but it should only be considered once for the final sum.

## Input Format
 
- The first line of input consists of integer N representing the number of rows and columns of the matrix.



## Output Format

- Print a single line of output consisting of the sum of the diagonal integers

---

## Constraints
- **1 ≤ N ≤ 10<sup>5</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
3 
```

**Output:**
```bash
5
```

### Explanation

The matrix is: <br>
1 1 1 <br>
1 1 1<br>
1 1 1<br>


Main diagonal sum: 1+1+1=3<br>
Secondary diagonal sum: 1+1+1=3<br>
But the center element (1) is counted twice, so we subtract 1.<br>
The total sum is 3+3−1=5.

## Sample Testcase 1

**Input:**
```bash
2
```

**Output:**
```bash
4
```

### Explanation

The matrix is:<br>
1 1<br>
1 1<br>


Main diagonal sum: 1+1=2<br>
Secondary diagonal sum: 1+1=2?<br>
The total sum is 2+2=4.<br>

---

## Solution (C++)

```cpp

#include <bits/stdc++.h>
using namespace std;

int diagonal_sum(int n) {
    int res = 2*n;
    if(n&1)
        res--;

    return res; // Placeholder return value
}

int main() {
    int n;
    cin >> n;
    
    int result = diagonal_sum(n);
    cout << result << endl;
    return 0;
}

```


Happy coding! 🚀
