# problem

count the number of arithmetic slices

[statement]()

# idea

track the length of each consecutive regions and accumulate the count

- space: `O(1)`
- time: `O(n)`

# code

```c++
int numberOfArithmeticSlices(vector<int>& A) { 
    int n = A.size();
    if(n<3) return 0;
    int d = A[1] - A[0], l = 0, r = 0;
    
    for(int i=1; i<n-1; i++){
        if(A[i+1] - A[i] == d)
            l++;
        else{
            if(l) r += ((1+l) * l / 2);
            l = 0;
            d = A[i+1] - A[i];
        }
    }
    
    return r += ((1+l) * l / 2);
}
```
