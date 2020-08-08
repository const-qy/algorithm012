> 二叉树的三种遍历方式（非递归）
1. 前序遍历
```cpp
vector<int> preorderTraversal(TreeNode* root){
  TreeNode* cur = root;
  stack<TreeNode*> stack;
  vector<int > res;
  while(cur || !stack.empty()){
     while(cur){
     res.push_back(cur->val);
     stack.push(cur);
     cur = cur->left;
     }
     cur = stack.top();
     stack.pop();
     cur = stack.top()->right;
     
     
  }
```
2. 中序遍历
```cpp
vector<int> inorderTraversal(TreeNode* root){
  TreeNode* cur = root;
  stack<TreeNode*> stack;
  vector<int > res;
  while(cur || !stack.empty()){
     while(cur){
     
     stack.push(cur);
     cur = cur->left;
     }
     cur = stack.top();
     stack.pop();
     res.push_back(cur->val);
     cur = cur->right;
    
  }
```
