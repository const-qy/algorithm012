```cpp
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
private:
	unordered_map<int, int> index;

public:
	TreeNode* my_buildTree(vector<int>& preorder,vector<int>& inorder ,int pre_left,int pre_right,int inorder_left,int inorder_right) {
		if (pre_left > pre_right) {
			return NULL;
		}
		//先序遍历序列的第一个元素，为根节点
		int preorder_root = pre_left;
		//在中序遍历中找到根节点；
		int inorder_root = index[preorder[preorder_root]];
		//建立根节点
		TreeNode* root = new TreeNode(preorder[preorder_root]);

		//左子树的节点数目 =
		int size_left_subtree = inorder_root - inorder_left;
	

		//得到左子树
		root->left = my_buildTree(preorder, inorder, pre_left + 1, pre_left + size_left_subtree, inorder_left, inorder_root - 1);
    //得到右子树
		root->right =my_buildTree(preorder, inorder, pre_left + size_left_subtree+1, pre_right, inorder_root+1, inorder_right);
		return root;

	}
	TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
		int length = preorder.size();
		for (int i = 0; i < length; i++) {
			index[inorder[i]] = i;
		}
		return my_buildTree(preorder,inorder,0,length-1,0,length-1);
	}
};
```
