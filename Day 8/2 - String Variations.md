## Problem Statement

You are given a string with alphabets. You need to convert the string to lowercase and check if the string is a palindromic one.

If the string is a palindrome, print the length of the palindromic string. If that string is a non-palindromic one, print the ASCII value of the first character of the alphabet in the given string.

## Input Format

- The input consists of a single string containing only alphabetic characters (both uppercase and lowercase). 

## Output Format

- Print the Length of the palindromic string if it is a palindrome after performing the above operations. Else print the ASCII value of the first character.

---

## Constraints
- **1 ≤ S ≤ 2*10<sup>5</sup>**

---

## Sample Testcase 0

**Input:**
```bash
ABABABA
```

**Output:**
```bash
7
```

### Explanation

Since the above string is a palindrome, the length is printed.

## Sample Testcase 1

**Input:**
```bash
AJDHHAKOEIE
```

**Output:**
```bash
65
```

### Explanation

Since the above string is not a palindrome, an ASCII value of A is printed, i.e., 65

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

int user_logic(const string& s) {
    bool upper = isupper(s[0]);
    int n = s.size();
    for(int i=0;i<n/2;i++){
        if(tolower(s[i]) != tolower(s[n-1-i])){
            int val = upper ? toupper(s[0]) : tolower(s[0]);
            return val;
        }
    }

    return n;
}

int main() {
    string s;
    getline(cin, s);

    // Call user logic function and print the output
    int result = user_logic(s);
    cout << result << endl;

    return 0;
}

```


Happy coding! 🚀
