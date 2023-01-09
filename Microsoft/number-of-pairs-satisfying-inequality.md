

# Code
```
class Solution {
public:

   long long int ans;
   
    void findCount(vector<int>& nums, int start, int mid, int end,int diff){
        int l = start, r = mid + 1;
        while(l <= mid && r <= end){
            if(nums[l]<=(nums[r]+diff)){
                ans += (end - r+1);
                l++;
            }
            else{
                r++;
            }
        }
        sort(nums.begin() + start, nums.begin() + end + 1); 
        return;
    }
    void mergeSort(vector<int>& nums, int start, int end,int diff){
        if(start == end) return;
        int mid = (start + end)/2;
        mergeSort(nums,start, mid,diff);
        mergeSort(nums,mid+1,end,diff);
        findCount(nums,start,mid,end,diff);
        return;  
    }

    long long numberOfPairs(vector<int>& a, vector<int>& b, int diff) {
        ans = 0;
        int n = a.size();
        vector<int>v(n);      
        for(int i=0;i<n;i++)
        v[i]=a[i]-b[i];               
        mergeSort(v,0,n-1,diff);
        return ans;
    }
};
```
