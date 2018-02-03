## [Question](https://leetcode.com/problems/same-tree/description/)
```c++
 /**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==NULL && q==NULL){return true;}
        if(!p || !q){return false;}
        if(p->val != q->val){return false;}
        else{
            return isSameTree(p->left,q->left) && isSameTree(p->right,q->right);
        }
    }
};
```

#### 常规题目，注意p q取数值之前，要判断其空不空！ 然后递归左右孩子。
#### 下面这个写法，天秀啊，牛逼，省事
```c++
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==NULL || q==NULL) return {p==q};
        else{
            return (p->val==q->val)&&(isSameTree(p->left,q->left))&&(isSameTree(p->right,q->right));
        }
    }
};
```
