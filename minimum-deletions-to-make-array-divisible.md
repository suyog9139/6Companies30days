

# Code
```
class Solution {
public:
    int minOperations(vector<int>& nums, vector<int>& numsDivide) {
        int count=0;
        bool flag = false;
        priority_queue <int, vector<int>, greater<int>>pq;
        for(int i=0; i<nums.size(); i++){
            pq.push(nums[i]);
        }
        int gc=numsDivide[0];
        for(int i=0; i<numsDivide.size(); i++){
            gc = __gcd(numsDivide[i],gc);
        }
        int prev=0;
        while(!pq.empty()){
            if(gc%pq.top()!=0){
                count++;
                pq.pop();
            }
            else{
                return count;
            }
        }
        return -1;
        
    }
};
```
