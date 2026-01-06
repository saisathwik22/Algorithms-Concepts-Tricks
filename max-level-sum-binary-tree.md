## Breadth First Search (BFS)
#### Use Queue in BFS Traversal
```
maxSum = intmin, finalLeve = 0;
queue<TreeNode*> q;
q.push(root);
currLevel = 1;
while(!q.empty()) {
  n = q.size();
  sum = 0;
  while(n--) {
    TreeNode* temp = q.front();
    q.pop();
    sum += temp->val;
    if(temp->left) q.push(temp->left);
    if(temp->right) q.push(temp->right);
  }
  if(sum > maxSum) {
    maxSum = sum;
    finalLevel = currLevel;
  }
  currLevel++;
}
return finalLevel;
```

## Depth First Search (DFS)
#### use inorder/preorder/postorder traversal
#### use map to store level and corresponding sum

```
map<int, int> mp;
void DFS(TreeNode* root, int level) {
  if(!root) return;
  mp[level] += root->val;

  DFS(root->left, level + 1)
  DFS(root->right, level + 1)
}

mp.clear();
DFS(root, 1);
maxSum = int min, resultLevel = 0;
for(auto it : mp) {
  int level = it.first;
  int sum = it.second;
  if(sum > maxSum) {
    maxSum = sum;
    resultLevel = level;
  }
}
return resultLevel;
```
