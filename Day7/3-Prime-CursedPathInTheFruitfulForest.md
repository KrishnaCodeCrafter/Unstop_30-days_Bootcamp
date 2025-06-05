## Problem Statement

In the Fruitful Forest, there is a grid of trees bearing the most delicious sweet fruits. These trees are arranged neatly in rows, and each row is carefully enclosed by a wire fence. 

The entrance to the forest is located at the top-left corner, and it's the only way to enter. To move deeper into the forest, one must follow a strict path:

- From the entrance, you must begin at the first tree in the top-left corner and travel to the end of the first row in right direction.
- Once you reach the end of the row, you must move down to the second row and continue your journey in left direction.
- This process repeats for every row in the forest, following a zig-zag pattern: top-left -> right-end -> down to second row -> left-end -> down to 3rd row and so on...

As you move through the grid, you need to check the number of fruits on each tree. If the number of fruits on a tree is a prime number, you must skip that tree and continue your journey, as those fruits are cursed. Only the trees with non-prime numbers of fruits are worth stopping for and collecting.

After completing the collection, print the list of non-prime numbers of fruits you encounter. If all numbers encountered are prime, print -1 to indicate that no non-prime fruits were found.

## Input Format
 
- The first line of input contains two space separated integer N and M denoting the diThe first line contains two space separated integers M and N representing the number of rows and columns of the forest grid, repectively.

- The next M lines contain N space separated integers each, representing the number of fruits on each tree in the forest grid.

## Output Format

- Print the non-prime numbers of fruits encountered during the zigzag traversal, separated by spaces. If no non-prime numbers are found, output -1.

---

## Constraints
- **1 ≤ M,N ≤ 50**  
- **1 ≤ matrix[i][j] ≤ 10<sup>4</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
2 2
2 3
5 7
```

**Output:**
```bash
-1
```

### Explanation

2* -> 3* -> 7* -> 5* ('*' means discard)<br>
All numbers are prime, so the output is -1.

## Sample Testcase 1

**Input:**
```bash
3 3
4 5 6
7 8 9
10 11 12
```

**Output:**
```bash
4 6 9 8 10 12
```

### Explanation

Traverse the forest in a zigzag pattern as specified, excluding prime numbers: 5, 7, 11<br>
4 -> 5* -> 6 -> 9 -> 8 -> 7* -> 10 -> 11* -> 12 ('*' means discard)<br>
The tree with non-prime numbers of fruits are: 4, 6, 9, 8, 10, 12.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

void zigzag_traversal(int m, int n, vector<vector<int>>& grid) {
    vector<bool> isPrime(10001,true);
    isPrime[0] = isPrime[1] = false;
    for(int i=2;i*i <= 10000;i++){
        if(isPrime[i]){
            for(int j=i*i;j<=10000;j+=i){
                isPrime[j] = false;
            }
        }
    }       
    bool val = true;
    
    int left =0,right = n-1;
    
    for(int i=0;i<m;i++){
        if(i&1){
            for(int j=right;j>=left;j--){
                if(!isPrime[grid[i][j]]){
                    val = false;
                    cout<<grid[i][j]<<" ";
                }
            }
        }else{
            for(int j=left;j<=right;j++){
                if(!isPrime[grid[i][j]]){
                    val = false;
                    cout<<grid[i][j]<<" ";
                }
            }
        }
    }

    if(val)
        cout<<-1<<endl;
    
}

int main() {
    int M, N;
    cin >> M >> N;
    vector<vector<int>> grid(M, vector<int>(N));
    for (int i = 0; i < M; ++i) {
        for (int j = 0; j < N; ++j) {
            cin >> grid[i][j];
        }
    }
    zigzag_traversal(M, N, grid);
    return 0;
}

```


Happy coding! 🚀
