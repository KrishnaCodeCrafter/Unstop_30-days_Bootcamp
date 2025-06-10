## Problem Statement

In a futuristic city, a powerful robot named Eon who wants to become unstoppable and was built with one mission: to achieve the highest energy level possible. Eon was given a range of power levels, from P to Q (inclusive), each representing units of energy he could absorb. But Eon had a unique ability, he could reverse the digits of any power level, altering its value.

Eon's goal was clear: he needed to combine these power levels to maximize his energy and become the most powerful entity in the city. He carefully analyzed each power level, choosing whether to keep it as it was or reverse it for a boost. With every calculated choice, Eon came closer to amassing the ultimate energy, ready to take control and rule the futuristic world with unmatched strength.

As Eon’s Boss, you guide him in his quest of dominance!

## Input Format

- The first line contains an integer P representing the start range.

- The second line contains an integer Q representing the end range.
 

## Output Format

- Print a single integer, the maximum energy level Eon can achieve in the quest of Dominance.

---

## Constraints

- **1 <= P < Q <= 10<sup>5</sup>**

---

## Sample Testcase 0

**Input:**
```bash
10 
12
```

**Output:**
```bash 
42
```

### Explanation

The given power levels are in range [10,12].<br>
10 - keep it original<br>
11 - original or reverse, doesn't matter!<br>
12 - reverse it to 21<br>
Sum - 10 + 11 + 21 = 42.


## Sample Testcase 1

**Input:**
```bash
31
35
```

**Output:**
```bash
192
```
### Explanation

The given power levels are in range [31,35].<br>
31 - keep it original<br>
32 - keep it original<br>
33 - original or reverse<br>
34 - reverse it - 43<br>
35 - reverse it - 53<br>
Sum - 31 + 32 + 33 + 43 + 53 = 192

---

## Solution (C++)

```cpp

#include <iostream>
using namespace std;

int rev(int num){
    int res = 0;
    while(num){
        int rem = num%10;
        res *= 10;
        res += rem;
        num /= 10;
    }
    return res;
}

int maxDigitReversalSum(int A, int B) {
    long long res = 0;
    for(int i=A;i<=B;i++){
        int val = rev(i);
        res += max(val,i);
    }

    return res;
}

int main() {
    int A, B;
    cin >> A >> B;

    int result = maxDigitReversalSum(A, B);
    cout << result << endl;

    return 0;
}


```


Happy coding! 🚀
