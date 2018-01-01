# problem

[statement](https://leetcode.com/problems/palindromic-substrings/description/)

# idea

denote `d[i][j]` as whether substring starting from `i` and end in `j` is a palindromic string, then:

- `d[i][j] = d[i+1][j-1]` if `s[i] = s[j]`
- `d[i][j] = 0` otherwise

# code

```c++
    int countSubstrings(string s) {
    int n = s.size(), r=n;
    int d[n][n];
    for(int i=0; i<n; i++){
        for(int j=0; j<n; j++)
            d[i][j] = 0;
        d[i][i] = 1;
    }
    
    for(int i=0; i<n; i++){ // end i
        for(int j=i-1; j>=0; j--) {// start j
            if(s[j] == s[i]){
                if((j+1) <= (i-1)) // boundary check
                    d[j][i] = d[j+1][i-1];                    
                else
                    d[j][i] = 1;
                r += d[j][i];
            }                
        }
    }
    return r;
}
```