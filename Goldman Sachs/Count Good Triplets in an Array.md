# Intuition
try by using segment tree

# Code
```
#include <ext/pb_ds/assoc_container.hpp>
#include <ext/pb_ds/tree_policy.hpp>
using namespace __gnu_pbds;
#define ordered_set tree<int, null_type,less<int>, rb_tree_tag,tree_order_statistics_node_update>
typedef long long ll;


class Solution {
public:
    long long goodTriplets(vector<int>& nums1, vector<int>& nums2) {
        unordered_map<ll,ll>mp;
        ordered_set pbds;
        ll count=0;
        ll n = nums1.size();

        for(int i=0; i<n; i++){
            mp[nums2[i]] = i;
        }
        vector<ll>left(n),right(n);
        for(int i=0; i<n; i++){
            ll curr = mp[nums1[i]];
            left[i] = pbds.order_of_key(curr);
            pbds.insert(curr);
        }
        pbds.clear();
        for(int i=n-1;i>=0; i--){
            ll curr = mp[nums1[i]];
            right[i] = pbds.size() - pbds.order_of_key(curr);
            pbds.insert(curr);
        }
        for(int i=1; i<n-1; i++){
            count += (left[i]*right[i]);
        }
        return count;

        
    }
};
```
