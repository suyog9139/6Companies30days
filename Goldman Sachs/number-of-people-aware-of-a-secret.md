

# Code
```
typedef long long ll;
class Solution {
public:
    int peopleAwareOfSecret(int n, int delay, int forget) {
        ll mod = 1e9 +7;
        ll dp[n+1];
        dp[0]=0;
        dp[1] = 1;
        ll ans=0;
        ll noofpeopleKSecret = 0;
        for(int i=2; i<=n; i++){
            ll noofnewpeopleKS = dp[max((i-delay),0)];
            ll noofpeopleforget = dp[max((i-forget),0)];
            noofpeopleKSecret+=(noofnewpeopleKS-noofpeopleforget+mod)%mod;
            dp[i] = noofpeopleKSecret;
        }

        for(int i= n-forget+1; i<=n; i++){
            ans=(ans+dp[i])%mod;
        }
        return ans;
    }
};
```
