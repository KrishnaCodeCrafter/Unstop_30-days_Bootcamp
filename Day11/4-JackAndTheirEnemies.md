## Problem Statement

Jack enjoys playing his favorite game, Enemy Exodus, which features N groups of enemies, with the i-th group containing group[i]  enemies.<br>
There's a critical point in the game: after M minutes, the enemies activate a super shield headquarters that makes them invulnerable. Jack knows this and wants to eliminate all enemies before the shield is activated.<br>
Each minute, he can decide on a kill rate K, which represents the number of enemies he will attempt to kill from a chosen group. If a group has fewer than K enemies, he will kill all remaining enemies in that group for that minute. Jack prefers to kill enemies slowly but must still finish off all of them before the shield activates.<br>
The task is to determine the minimum integer value of K that allows him to kill all enemies within the M minutes and convert this value into octal format.

## Input Format

- Each test case consists of three lines of input.
- The first line contains the integer N, representing the number of groups of enemies.
- The second line includes Nspace-separated integers, representing the number of enemies in each group.
- The third line provides the integer M, indicating the number of minutes Jack has before the enemies activate their shield.

## Output Format

- Print the minimum integer K followed by K in an octal number. If no such min value exists, print 1.

---

## Constraints

- **1<=N<=10<sup>4</sup>**
- **N<=M<=10<sup>6</sup>**
- **1<=group[i]<=10<sup>6</sup>**

---

## Sample Testcase 0

**Input:**
```bash
4 
3 6 7 11
8
```

**Output:**
```bash 
4 4
```

### Explanation

The lower index value here is 4, which, when converted to octal, gives 4

## Sample Testcase 1

**Input:**
```bash
5 
30 11 23 4 20
5
```

**Output:**
```bash
30 36
```
### Explanation

The minimum value here is 30, which, when converted to octal, gives 36

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

bool check(vector<int>& arr,int k,int mid){
    int n = arr.size();
    int cnt =0 ;
    for(auto &x:arr){
        cnt += ceil((double)x/mid);
    }
    return cnt <= k;
}

void user_logic(int n, vector<int>& enemy_groups, int m) {
    int low = 1;
    int high = accumulate(enemy_groups.begin(),enemy_groups.end(),0);
    int ans=-1;
    while(low <= high){
        int mid = low + (high - low)/2;
        if(check(enemy_groups,m,mid)){
            high = mid-1;
            ans = mid;
        }
        else
            low = mid+1;
    }
    cout<<ans<<" ";
    cout<<oct<<ans;
}

int main() {
    int n, m;
    cin >> n;
    vector<int> enemy_groups(n);
    for (int i = 0; i < n; ++i) {
        cin >> enemy_groups[i];
    }
    cin >> m;
    
    user_logic(n, enemy_groups, m);
    
    return 0;
}

```


Happy coding! 🚀
