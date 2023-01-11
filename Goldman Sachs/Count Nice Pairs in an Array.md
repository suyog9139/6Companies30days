

# Code
```
class Solution {
public:
    int countNicePairs(vector<int>& nums) {
        int mod = 1e9+7;
        unordered_map<int,long long int>mp;
        long long int count=0;
        for(int i=0; i<nums.size(); i++){
            long long int n=nums[i];
            long long int k = 0;
            while(n!=0){
                k = k*10 + n%10;
                n= n/10;
            }
            // nums[i]=nums[i]-k;
            if(mp.find(nums[i]-k)!=mp.end()) count+=mp[nums[i]-k]%mod;
            mp[nums[i]-k]++;

            
        }
        return count%mod;
        
    }
};
```
