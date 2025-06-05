## Problem Statement

In a forest grid, there is a treasure chest guarded by a beast. A hero must collect keys scattered across the forest to unlock the chest. The task is to determine whether the hero can unlock the treasure chest and, if so, the shortest path to do so.

The hero can only reach the chest if they collect all keys first. Obstacles in the forest prevent movement.

Grid Symbols:

'H': Represents the hero's starting position.<br>
'C': Represents the treasure chest's position.<br>
'K': Represents a key that must be collected.<br>
'O': Represents an obstacle that blocks movement.<br>
'P': Represents a path the hero can move on.<br>

Rules:

- The hero must collect all the keys ('K') before they can reach the treasure chest ('C').
- The hero can move in four directions: up, down, left, and right.
- If it's not possible to collect all keys or reach the chest, return "Impossible".
- If it is possible to unlock the chest, return the minimum number of steps/length of shortest path required for the hero to collect all keys and reach the chest.

Note: Once we reach 'C' we can't move further.

## Input Format
 
- The first line of input contains two space separated integer N and M denoting the dimensions of the grid.

- The next N line each containing M space separated characters representing a 2D array of size NxM where each cell contains one of the following symbols:

- 'H': Hero's starting position (appears exactly once).

- 'C': Treasure chest (appears exactly once).

- 'K': Key(s) to be collected (at least one 'K' is guaranteed).

- 'O': Obstacle that blocks movement.

- 'P': Path the hero can move on.


## Output Format

- If the hero can collect all keys and reach the chest, output a single integer denoting the minimum number of steps/length of shortest path required.

- If it is not possible to collect all keys and reach the chest, output "Impossible".

---

## Constraints
- **1 ≤ N,M ≤ 20**  
- **1 ≤ N*M ≤ 40**  

---

## Sample Testcase 0

**Input:**
```bash
4 4
H P K O
O P O P
P K C P
O O P O
```

**Output:**
```bash
6
```

### Explanation

H->P->K : 2 steps<br>
backtrack to P : 1 step<br>
P->P->K->C : 3 steps<br>
Total 6 steps.

## Sample Testcase 1

**Input:**
```bash
3 3
P P P
O C K
H P O
```

**Output:**
```bash
Impossible
```

### Explanation

The hero must not cross the chest (C) in order to collect the key, so even if a direct path to the chest exists, the hero cannot collect the key, making the task impossible.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

bool isValid(int i,int j,int n,int m,vector<vector<char>>& grid){
    return (i>=0 && j>=0 && i<n && j<m && grid[i][j] != 'O');
}

int find_shortest_path(vector<vector<char>>& grid, int n, int m) {
    int start_x = -1;
    int start_y = -1;
    int total_keys = 0;
    int key_number = 0;
    vector<vector<int>> vec(n,vector<int>(m,0));

    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            if(grid[i][j] == 'H'){
                start_x = i;
                start_y = j;
            }else if(grid[i][j] == 'K'){
                vec[i][j] = key_number++;
                total_keys++;
            }
        }
    }

    int hasAllKeys = (1<<total_keys)-1;
    queue<vector<int>> que;
    vector<vector<vector<bool>>> visited(n,vector<vector<bool>>(m,vector<bool>(1<<total_keys,false)));
    visited[start_x][start_y][0] = true;
    que.push({start_x,start_y,0,0});

    vector<vector<int>> dir = {{0,1},{0,-1},{1,0},{-1,0}};

    while(!que.empty()){
        int x = que.front()[0];
        int y = que.front()[1];
        int steps = que.front()[2];
        int keys = que.front()[3];
        que.pop();
        // cout<<x<<" "<<y<<" "<<steps<<" "<<keys<<endl;

        if(grid[x][y] == 'C' && keys == hasAllKeys){
            return steps;
        }
        for(int i=0;i<4;i++){
            int new_x = x + dir[i][0];
            int new_y = y + dir[i][1];
            if(isValid(new_x,new_y,n,m,grid)){
                int new_keys = keys;
                if(grid[new_x][new_y] == 'K'){
                    new_keys = new_keys | (1<<vec[new_x][new_y]);
                }
                if(!visited[new_x][new_y][new_keys]){
                    if(grid[new_x][new_y] == 'C' && new_keys != hasAllKeys)
                        continue;
                    visited[new_x][new_y][new_keys] = true;
                    que.push({new_x,new_y,steps+1,new_keys});
                }
            }
        }

    }
    return -1;
}
int main() {
    int n, m;
    cin >> n >> m;
    vector<vector<char>> grid(n, vector<char>(m));
    
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> grid[i][j];
        }
    }
    
    int result = find_shortest_path(grid, n, m);
    if(result == -1){
        cout<<"Impossible"<<endl;
    }else{
        cout<<result<<endl;
    }

    return 0;
}


```


Happy coding! 🚀
