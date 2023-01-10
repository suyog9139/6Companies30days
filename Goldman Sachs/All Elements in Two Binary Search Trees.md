

# Code
```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> getAllElements(TreeNode* root1, TreeNode* root2) {
        stack<TreeNode*>st1,st2;
        vector<int>res;
        while(1){
            if(root1){
                st1.push(root1);
                root1=root1->left;
            }else if(root2){
                st2.push(root2);
                root2=root2->left;
            }else if(!st1.empty() && !st2.empty()){
                root1=st1.top();
                root2=st2.top();
                if(root1->val==root2->val){
                    res.push_back(root1->val);
                    res.push_back(root2->val);
                    st1.pop();st2.pop();
                    root1=root1->right;
                    root2=root2->right;
                }else if(root1->val<root2->val){
                    st1.pop();
                    res.push_back(root1->val);
                    root1=root1->right;
                    root2=NULL;
                }else if(root1->val>root2->val){
                    st2.pop();
                    res.push_back(root2->val);
                    root2=root2->right;
                    root1=NULL;
                }
            }else if((!st1.empty()&&root2==NULL) || (!st2.empty()&&root1==NULL)){
                    if(!st1.empty()){
                        root1=st1.top();
                        res.push_back(root1->val);
                        st1.pop();
                        root1=root1->right;
                    }else if(!st2.empty()){
                        root2=st2.top();
                        res.push_back(root2->val);
                        st2.pop();
                        root2=root2->right;
                    }
            }else{
                break;
            }
        }
        return res;
    }
};
```
