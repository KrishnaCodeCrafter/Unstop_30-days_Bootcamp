## Problem Statement

Prakash had a dream about a planet named IZOCXUL, where only lowercase letters exist. He gave you a string S from that planet, and your task is to find how many substrings of length 2 to K consist of unique characters only.

## Input Format
 
- The first line contains a string S, representing the string from this planet.

- The Second line consists of an integer K.

## Output Format

- Print K-1 lines where each line denotes the count of substring of size, from 2 to K.

---

## Constraints
- **|S| ≤ 10<sup>3</sup>**  
- **2 ≤ K ≤ |S|**  
- **NOTE : |S| denotes the length of the string.**  

---

## Sample Testcase 0

**Input:**
```bash
aabce
4
```

**Output:**
```bash
3
2
1
```

### Explanation

Given K = 4 and string - 'aabce

Substrgin of length 2 with unique characters are (ab), (bc) and (ce), Count - 3<br>
Substrgin of length 3 with unique characters are (abc) and (bce), Count - 2<br>
Substrgin of length 4 with unique characters are (abce), Count - 1

## Sample Testcase 1

**Input:**
```bash
a b c
3
```

**Output:**
```bash
2
1
```

### Explanation

Given K = 3 and string - 'abc'


Substrgin of length 2 with unique characters are (ab) and (bc), Count - 2<br>
Substrgin of length 3 with unique characters are (abc), Count - 1

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

vector<int> count_substrings(const string& str, int k) {
    vector<int> vec(k+1,0);
    int n = str.size();
    for(int i=0;i<n;i++){
        unordered_set<char> st;
        for(int j=0;j<k && i+j<n ; j++){
            char ch = str[i+j];
            if(st.find(ch) != st.end())
                break;
            st.insert(ch);
            if(j+1 >= 2){
                vec[j+1]++;
            }
        }
    }

    return vec;
}

int main() {
    string S;
    int K;
    cin >> S;
    cin >> K;
    vector<int> result = count_substrings(S, K);
    for (int i=2;i<=K;i++) {
        cout << result[i] << endl;
    }
    return 0;
}

```


Happy coding! 🚀
