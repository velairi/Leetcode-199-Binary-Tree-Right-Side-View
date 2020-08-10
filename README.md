# Leetcode-199-Binary-Tree-Right-Side-View
https://leetcode.com/problems/binary-tree-right-side-view/

```
Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

Example:

Input: [1,2,3,null,5,null,4]
Output: [1, 3, 4]
Explanation:

   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
  
```

Approach: 

0. Initialize currentLevel array with the first node.
1. Add nodes per level into currentLevel array, then add it's children to the nextLevel array.
2. Add last node in currentLevel array to the output array
3. Set currentLevel array with nextLevel array so that we look at the children.
4. Repeat until we don't find anymore children.
5. Return output array which contains the rightmost children.


```
    func rightSideView(_ root: TreeNode?) -> [Int] {
        var currentLevel = [root]
        var nextLevel = [TreeNode?]()
        var output = [Int]()
        while !currentLevel.isEmpty {
            nextLevel = []
            for element in currentLevel {
                if let left = element?.left {
                    nextLevel.append(left)
                }
                if let right = element?.right {
                    nextLevel.append(right)
                }
            }
            var lastIndex = currentLevel.count - 1
            if let last = currentLevel.removeLast() {
                output.append(last.val)
            }
            currentLevel = nextLevel
        }
        return output
    }
```

Runtime: 8 ms, faster than 98.31% of Swift online submissions for Binary Tree Right Side View.
Memory Usage: 21 MB, less than 28.81% of Swift online submissions for Binary Tree Right Side View.
