# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
pick nonpick approach same as combination I problem


# Code
```
class Solution {
public:
    void findcombination3(int ind,int k, int n, vector<vector<int>>&ans,vector<int>&ds){
        if(ind==10||k==0){
            if(n==0 && k==0){
                ans.push_back(ds);
            }
            return;
        }
        if(n>=ind && k>0){
            ds.push_back(ind);
            findcombination3(ind+1,k-1,n-ind,ans,ds);
            ds.pop_back();
        }
        findcombination3(ind+1,k,n,ans,ds);
    }

    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>>ans;
        vector<int>ds;
        findcombination3(1,k,n,ans,ds);
        return ans;
    }
};
```
