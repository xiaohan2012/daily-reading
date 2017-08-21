# problem

[statement]()

# dp idea

`d[i]` keeps track of the maximum chain length up to position `i`
  - does not have to include `pairs[i]`

need to sort the array, otherwise, will miss certain combinations. 

for example:

`[(3, 4), (1, 2)]` if unsorted, returns 1, but the true answer is 2

# code

```c++
    int findLongestChain(vector<vector<int>>& pairs) {
        int n = pairs.size();        
        if(n==0) return 0;
        sort(pairs.begin(), pairs.end());        
        vector<int> d(n, 1); // the maximum length up to position i
        for(int i=1; i<n; i++){
            for(int j=i-1; j>=0; j--)
                d[i]= max(d[i], (pairs[i][0] > pairs[j][1] ? d[j]+1 : d[j])); // this is the essense
        }
        return d[n-1];
    }
```