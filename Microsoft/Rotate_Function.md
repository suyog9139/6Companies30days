# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
in general
arr = [a,b,c,d]
S0= 0a+1b+2c+3d
s1= 0d+1a+2b+3c
s2 =---
s3= ---

relation in s0 and s1
s1 = s0 + sum of array - n*(arr[n-1-i]);

# Code
```
class Solution {
public:
    int maxRotateFunction(vector<int>& nums) {
        int sum=0;
        int res=0;
        int n = nums.size();
        for(int i=0; i<n; i++){
            res=res+(i*nums[i]);
            sum=sum+nums[i];
        }
        int ans = res;
        for(int i=0; i<n; i++){
            res = res + sum - n*(nums[n-1-i]);
            ans= max(ans,res);
        }
        return ans;
    }
};
```
