# Definition
Approporate for Algoexpert
```python
class BinaryTree:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
```

## Traversing tree
We have 3 types of deep traversing of the binary tree:
* pre-order
* in-order
* post-order

```python
def dfs_preorder(root: BinaryTree) -> List:
    if not root:
        return []
    return [root.val] + dfs_preorder(root.left) + dfs_preorder(root.right)


def dfs_inorder(root: BinaryTree) -> List:
    if not root:
        return []
    return dfs_inorder(root.left) + [root.val] + dfs_inorder(root.right)


def dfs_postorder(root: BinaryTree) -> List:
    if not root:
        return []
    return dfs_postorder(root.left) + dfs_postorder(root.right) + [root.val]
```
We might also traverse the binary tree level by level. It this case we say about breath search algorithm. To achieve this we use deque.
```python
def bfs(root: BinaryTree) -> List:
    if not root:
        return []
    queue = deque([root])
    result=[]
    while queue:
        node = queue.popleft()
        result.append(node.val)
        if node.left:
            queue.append(node.left)
        elif node.right:
            queue.append(node.right)
    return result
```

# Challenges
## Branch Sums
**challenge info**
| Title       | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|-------------|------------|----------------|--------------|------------|-----------------|------------------|
| Branch Sums | AlgoExpert | Binary Tree    | recursion    | easy       | O(n)            | O(n)            |
#### Idea 
* recursive call dfs or the left and right childeren
* base case: if Node is None

```python
def dfs(root: BinaryTree, running_sum, sum_per_branch) -> List | None:
    if not root:
        return
    new_sum = running_sum + root.val
    if not root.left and not root.right:
        sum_per_branch.append(new_sum)
        return
    dfs(root.left, new_sum, sum_per_branch)
    dfs(root.right, new_sum, sum_per_branch)


def branch_sums(root: BinaryTree) -> List:
    brunch_sums = []
    dfs(root, 0, brunch_sums)
    return brunch_sums
```
## Node Depth
**challenge info**
| Title       | Source     | Data Structure | Algo Concept | Difficulty | Time Complexity | Space Complexity |
|-------------|------------|----------------|--------------|------------|-----------------|------------------|
| Node Depths | AlgoExpert | Binary Tree    | Recursion    | easy       | O(n)            | O(h)             |

Of course h is hight of the tree.

```python
 def node_depths(root: BinaryTree,depth=0) -> int:
     if not root:
         return 0
     return depth+node_depths(root.left,depth+1)+node_depths(root.right,depth+1)
```