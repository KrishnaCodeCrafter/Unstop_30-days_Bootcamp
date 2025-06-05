## Problem Statement

In a distant galaxy, a young inventor named Leo created a robot called "Trace" to help him find hidden treasures. These treasures were marked on ancient maps stored as long strings of mysterious text. To locate a treasure, Trace needed to find a specific clue called the Key, made up of a unique combination of characters.

The maps were massive and full of random symbols, making Trace’s task difficult. The Key could appear in any part of the map, but its characters might be jumbled. Trace’s job was to find the shortest section(substring) of the map that included all the characters of the Key, no matter the order.  If no such substring exists, Trace should return -1.

## Input Format

- The first line contains a string S representing the map.

- The second line contains a string T representing the Key.

## Output Format

- Output the length of the shortest substring of s that contains all the characters of t in any order. If no such substring exists, output -1.

---

## Constraints

- **Each character of S and T is a printable ASCII character.**
- **1 ≤ |S| ≤ |T| ≤ 10<sup>5</sup>**

---

## Sample Testcase 0

**Input:**
```bash
warrmioruhk
warrior
```

**Output:**
```bash
8
```

### Explanation

The shortest substring of S that contains all the characters of T is "warrmior", which has length 8.

## Sample Testcase 1

**Input:**
```bash
Thunder
King
```

**Output:**
```bash
-1
```

### Explanation

There is no substring of S that contains all the characters of T.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int shortest_substring(const string& s, const string& t) {
    int n = s.size();
    int left=0;
    int minLen = INT_MAX;
    int right = 0;
    vector<int> freq(128,0);
    for(auto &x:t){
        freq[x]++;
    }
    int cnt = t.size();
    while(right < n){
        char r_ch = s[right];
        if(freq[r_ch] > 0){
            cnt--;
        }
        freq[r_ch]--;
        while(cnt == 0){
            minLen = min(minLen,right-left+1);
            char l_ch = s[left];
            freq[l_ch]++;
            if(freq[l_ch] > 0){
                cnt++;
            }
            left++;
        }
        right++;
    }
    if(minLen != INT_MAX)
        return minLen;
    return -1;
}

int main() {
    string s, t;
    cin >> s >> t;
    int result = shortest_substring(s, t);
    cout << result << endl;
    return 0;
}


```


Happy coding! 🚀
