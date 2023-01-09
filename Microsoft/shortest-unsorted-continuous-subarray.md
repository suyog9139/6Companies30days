

# Code
```
class Solution {
public:
    int findUnsortedSubarray(vector<int>& nums) {
        int n = nums.size();
        int low=0; 
        int high = n-1;
        while(low+1<n && nums[low]<=nums[low+1]) low++;
        while(high-1>=0 && nums[high]>=nums[high-1]) high--;

        if(low==n-1) return 0;
        int submx=INT_MIN, submi=INT_MAX;
        for(int i=low; i<=high; i++){
            submx = max(submx, nums[i]);
            submi = min(submi, nums[i]);
        }

        while(low-1>=0 && nums[low-1]>submi) low--;
        while(high+1<n && nums[high+1]<submx) high++;

        return high-low+1;
    }
};
```
