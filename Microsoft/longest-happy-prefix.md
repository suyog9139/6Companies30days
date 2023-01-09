

# Code
```
class Solution {
public:
    string longestPrefix(string s) {
        int n = s.size();

        if(n==1){
            return "";
        }
        long long int p = 31;
        long long int mod = 1000000007;
        long long int pow = 1;

        long long ph = 0;
        long long sh = 0;
        int ans =0;
        for(int i=0; i<n-1; i++){
            ph = ((ph*p) + (s[i]-'a'+1))%mod;
            sh = (sh + ((s[n-1-i]-'a'+1)*pow)%mod)%mod;

            pow = (pow*p)%mod;
            if(ph==sh) ans=i+1;
        }
        return s.substr(0,ans);

        
    }
};
```
