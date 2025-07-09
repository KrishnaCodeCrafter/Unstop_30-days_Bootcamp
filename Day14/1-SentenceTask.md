## Problem Statement

Mohit’s teacher presented him with a Challenging task: to unscramble a sentence using specific guidelines. The sentence is provided as a list of words, each separated by single spaces. Each word must be rearranged according to its 1-indexed word position.

For example, the phrase "This is a sentence" could be transformed into "SENTENCE4 IS2 A3 THIS1".

Mohit’s teacher assigned him the Task of reconstructing the original sentence from these scrambled pieces, ensuring the final sentence has no more than 9 words. Mohit, being a supportive friend, took on the challenge to help Rohit complete the assignment given by his teacher

Note: S consists of lowercase and uppercase English letters, spaces, and digits from 1 to 9. The words in S are separated by a single space. S contains no leading or trailing spaces.

## Input Format

- Input line will contain the string.

## Output Format

- Ouput the string according to the given condition in problem statement.

---

## Constraints

- **2 <= S.length <= 200**

---

## Sample Testcase 0

**Input:**
```bash
World2 Hello1
```

**Output:**
```bash 
Hello World
```

### Explanation

In this test case, the input sentence "Hello World" is scrambled according to the given rules.


The word "World" is at position 2 in the original sentence, and "Hello" is at position 1.


The scrambled sentence is rearranged to form the original sentence "Hello World."

## Sample Testcase 1

**Input:**
```bash
industries5 transforming4 are3 models2 AI1
```

**Output:**
```bash
AI models are transforming industries
```
### Explanation

In this test case, the input sentence "AI models are transforming industries" is scrambled using the provided rules.


Each word is correctly numbered and rearranged, resulting in the original sentence being reconstructed: "AI models are transforming industries"

---

## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;

void sort_sentence(string& s) {
    map<int,string> umap;
    istringstream iss(s);
    string word;
    while(iss >> word){
        int idx = word.back() - '0';word.pop_back();
        umap[idx] = word;
    }    

    string str;
    for(auto& x:umap){
        str += x.second;
        str += " ";
    }
    cout<<str<<endl;
}

int main() {
    string s;
    getline(cin, s);
    
    sort_sentence(s);
    
    return 0;
}

```


Happy coding! 🚀
