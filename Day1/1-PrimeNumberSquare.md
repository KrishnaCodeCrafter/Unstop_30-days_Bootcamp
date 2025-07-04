## Problem Statement

Given a number N. Your task is to create a program to calculate the N-th term of the Alice choice.

Alice's sequence consists of the squares of prime numbers: 2^2, 3^2, 5^2, 7^2, 11^2,13^2,17^2,19^2, 23^2, 29^2,…………

## Input Format

- The first line should contain only one line input given as number N.

## Output Format

- Output the square of the prime number at the N-th position in the sequence.

---

## Sample Testcase 0

**Input:**
```bash
10
```

**Output:**
```bash
841
```

### Explanation

The Nth term is 841 It is one-based indexing, and by observing the pattern of the sequence then, all numbers are prime numbers and have to calculate the 10th term. So, The 10th number is 29, and its square is 841.

## Sample Testcase 1

**Input:**
```bash
3
```

**Output:**
```bash
25
```

### Explanation

The Nth term is 25 It is one-based indexing, and by observing the pattern of the sequence then, all numbers are prime numbers and have to calculate the 3rd term. <br>
So, the 3rd number is 5, and its square is 5^2 is 25. <br>
Sequence: 2, 3, 5 <br>
Index.       : 1, 2, 3

---

## Constraints
- **1 ≤ N ≤ 10<sup>5</sup>**  
---


## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;

bool isPrime(int n){
    if(n < 2)
        return false;
    for(int i=2;i<=sqrt(n);i++){
        if(n%i == 0)
            return false;
    }
    return true;
}

int prime(int n){
    int val = 0;
    int prime_cnt = 0;
    while(true){
        if(isPrime(val))
            prime_cnt++;
        if(prime_cnt == n)
            break;
        val++;
    }
    return val;
}

int main() {
    int n;
    cin>>n;

    int num = prime(n);
    cout<<num*num<<endl;    

    return 0;
}
```


Happy coding! 🚀
