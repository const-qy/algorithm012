# 迭代法
```cpp
class Solution {
public:
	vector<int> inorderTraversal(TreeNode* root) {
		stack<TreeNode*> s;
		vector<int> res;
		TreeNode* cur = root;
		while (cur ||s.size()) {

			while (cur)
			{
				s.push(cur);
				cur = cur->left;
				
			}
			cur = s.top();
			s.pop();
			res.push_back(cur->val);
			cur = cur->right;

		}
		return res;
	}
};
```
# 递归法
```
class Solution {
    vector<int> res;
public:
    vector<int> inorderTraversal(TreeNode* root) {
        
        if(root == NULL)
           return res;
        inorderTraversal(root->left);
        res.push_back(root->val);
        inorderTraversal(root->right);

        return res; 

    }
};
```
