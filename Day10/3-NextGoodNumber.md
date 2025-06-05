## Problem Statement

A good number is a number that contains all odd digits in it like 1113 is a good number because all the digits are odd.

You are given a number x you need to tell the next largest number which is greater than x and a good number.

## Input Format

- The first line will contain T, the number of test cases. The description of T test cases follows.

- Each line contains an integer x.

## Output Format

- For each test case, you need to print the next greatest good number.


---

## Constraints

- **1<=T<=10<sup>6</sup>**
- **1<=x<=10<sup>6</sup>**

---

## Sample Testcase 0

**Input:**
```bash
1
11
```

**Output:**
```bash
13
```

### Explanation

13 is the next greatest number of 11 which contains all odd digits.

## Sample Testcase 1

**Input:**
```bash
2
26
16
```

**Output:**
```bash
31
17
```

### Explanation

31 is the next greatest number of 26 which contains all odd digits. 17 is the next greatest number of 16 which contains all odd digits

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

void next_good_number(int x) {
    x++;
    string s = to_string(x);
    for(int i=0;i<s.size();i++){
        int num = s[i]-'0';
        if(!(num&1)){
            s[i]+=1;
            for(int j=i+1;j<s.size();j++){
                s[j] = '1';
            }
            break;
        }
    }
    cout<<s<<endl;
}

int main() {
    int T;
    cin >> T;
    vector<int> results(T);

    for (int i = 0; i < T; ++i) {
        int x;
        cin >> x;
        next_good_number(x);
    }

    return 0;
}

```


Happy coding! 🚀
