## Problem Statement

Three participants attended a math competition. In each round, two participants solved a problem:

- The correct solver gets 2 points.
- If both solve it correctly, each gets 1 point.
- If neither solves it, each gets 0 points.

Given final scores s1, s2, and s3, determine the maximum number of problems where both participants solved it correctly. If it's impossible to achieve these scores, output -1.

## Input Format

- The first line of input contains 3 space separated integers s1,s2 and s3 representing final scores of all the three participants.


## Output Format

- Print the maximum number of problems where two participants solved the question correctly. If it's impossible to achieve the given scores, output -1.


---

## Constraints

- **0<=s1<=s2<=s3<=5*10<sup>2</sup>**

---

## Sample Testcase 0

**Input:**
```bash
0 2 2
```

**Output:**
```bash 
2
```

### Explanation

Participant 1 has 0 points, so they did not win any games. Participants 2 and 3 each have 2 points, which can be achieved if they played two games against each other and both solved the problem correctly in each game, earning 1 point each per game.

## Sample Testcase 1

**Input:**
```bash
1 1 1
```

**Output:**
```bash
-1
```
### Explanation

It's impossible to achieve scores of 1, 1, and 1 for all three participants. Given the scoring rules, no valid sequence of games can result in all participants having exactly 1 point.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;


int main() {
    int a,b,c;
    cin>>a>>b>>c;

    if((a+b+c)%2)
        cout<<"-1\n";
    else{
        cout<<((a+b+c) - max(0,(c-b-a))) /2<<"\n";
    }

    return 0;
}

```


Happy coding! 🚀
