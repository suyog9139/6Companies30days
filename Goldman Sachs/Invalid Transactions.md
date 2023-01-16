# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    vector<string> invalidTransactions(vector<string>& transactions) {
        vector<int>time;
        vector<int>amount;
        vector<string>city;
        vector<string>ans;
        vector<string>name;

        int flag=0;
        for(auto it: transactions){
            stringstream ss(it);
            string str;

            while(getline(ss,str,',')){
                if(flag==0){
                    name.push_back(str);
                    flag=1;
                }
                else if(flag==1){
                    time.push_back(stoi(str));
                    flag=2;
                }
                else if(flag==2){
                    amount.push_back(stoi(str));
                    flag=3;
                }
                else if(flag==3){
                    city.push_back(str);
                    flag=0;
                }
            }
        }
        for(int i=0; i<amount.size(); i++){
            if(amount[i]>1000) ans.push_back(transactions[i]);
        }

        for(int i=0; i<transactions.size(); i++){
            for(int j=0; j<transactions.size(); j++){
                if(i==j) continue;
                if(name[i]==name[j] && city[i]!=city[j]){
                    if(abs(time[i]-time[j])<=60){
                        if(amount[i]<=1000){
                            ans.push_back(transactions[i]);
                            break;
                        }
                        
                    }
                }
            }
        }
        return ans;



    }
};
```
