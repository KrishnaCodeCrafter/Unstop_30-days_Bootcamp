## Problem Statement

In Unstop's  magical kingdom, a messenger must navigate a treacherous enchanted grid to deliver an urgent message to the royal palace. The grid is an ancient map, where each cell contains a rune that dictates the direction of movement:

a: Move 1 unit right; b: Move 1 unit left; c: Move 1 unit down; d: Move 1 unit up.

The messenger starts at the top-left corner of the map (0, 0) and must reach the palace at the bottom-right corner (m−1,n−1). However, the map's runes have been corrupted over time, and not all paths lead to the destination.

The messenger can use his magical power  to alter any rune, but each alteration consumes precious mana, costing 1 unit per change. The messenger must find the minimum mana required to adjust the map so that at least one path leads to the palace.

Will the messenger succeed in delivering the message in time? Your task is to determine the minimum mana required to ensure they reach their destination!

## Input Format
 
- The first line contains two space separated integers M and N, representing the rows and columns of the grid.

- The next N line each containing M values, a, b c, d.


## Output Format

- Print an integer representing the minimum cost (mana) required to ensure there is at least one valid path from the top-left corner to the bottom-right corner.


---

## Constraints
- **1 ≤ N,M ≤ 10<sup>3</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
3 3
a a b
c a d
b b c
```

**Output:**
```bash
2
```

### Explanation

Starting from the top-left cell (0, 0):<br>
Cell (0, 0): a (right), no cost to move to (0, 1).<br>
Cell (0, 1): a (right), no cost to move to (0, 2).<br>
Cell (0, 2): b (left), modify to move down to (1, 2) at a cost of 1.<br>
Cell (1, 2): d (up), modify to move down to (2, 2) at a cost of 1.<br>
Cell (2, 2): Destination reached.

## Sample Testcase 1

**Input:**
```bash
4 4
a b c d
b b a c
c c d b
d a a a
```

**Output:**
```bash
2
```

### Explanation

Cell (0, 0): a (right), no cost to move to (0, 1).<br>
Cell (0, 1): b (left), modify to move down to (1, 1) at a cost of 1.<br>
Cell (1, 1): b (left), modify to move down to (2, 1) at a cost of 1.<br>
Cell (2, 1): c (down), no cost to move to (3, 1).<br>
Cell (3, 1): a (right), no cost to move to (3, 2).<br>
Cell (3, 2): a (right), no cost to move to (3, 3).<br>
Cell (3, 3): Destination reached.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

/*
a -> right  {0,1}
b -> left   {0,-1}
c -> down   {1,0}
d -> up     {-1,0}
*/

int min_mana(vector<vector<char>>& grid) {
    int n = grid.size();
    int m = grid[0].size();
    vector<vector<int>> dir = {{0,1},{0,-1},{1,0},{-1,0}};
    vector<char> dir_char = {'a','b','c','d'};

    vector<vector<int>> vec(n,vector<int>(m,INT_MAX));
    vec[0][0] = 0;
    deque<pair<int,int>> dq;
    dq.push_back({0,0});

    while(!dq.empty()){
        int i = dq.front().first;
        int j = dq.front().second;
        dq.pop_front();

        for(int k=0;k<4;k++){
            int new_i = i + dir[k][0];
            int new_j = j + dir[k][1];

            if(new_i >= 0 && new_j >= 0 && new_i < n && new_j < m){
                int cost = ((grid[i][j] == dir_char[k])?0:1);
                if(cost + vec[i][j] < vec[new_i][new_j]){
                    vec[new_i][new_j] = vec[i][j] + cost;
                    if(cost == 0){
                        dq.push_front({new_i,new_j});
                    }else
                        dq.push_back({new_i,new_j});
                }
            }
        }


    }
    return vec[n-1][m-1];
}

int main() {
    int m, n;
    cin >> m >> n;
    
    vector<vector<char>> grid(m, vector<char>(n));
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            cin >> grid[i][j];
        }
    }
    
    int result = min_mana(grid);
    cout << result << endl;
    
    return 0;
}

```


Happy coding! 🚀
