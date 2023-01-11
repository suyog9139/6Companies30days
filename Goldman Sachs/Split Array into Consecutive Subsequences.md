#Code
```
class Solution {
public:
    bool isPossible(vector<int>& nums) {
        int count = nums.size();
        unordered_map<int,int>mp;
        for(int i=0; i<nums.size(); i++){
            mp[nums[i]]++;
        }
        for(int i=0; i<nums.size(); i++){
            int k = nums[i];
            if(mp[k]&&mp[k+1]&&mp[k+2]){
                mp[k]--;mp[k+1]--;mp[k+2]--;
                k+=3;
                count-=3;
                while(mp[k]>0 && mp[k]>mp[k-1]){
                    count--;
                    mp[k]--;
                    k++;
                }
            }
        }
        return count==0;
    }
};
```
