# Leetcode-199-Binary-Tree-Right-Side-View
https://leetcode.com/problems/binary-tree-right-side-view/

Runtime: 8 ms, faster than 98.31% of Swift online submissions for Binary Tree Right Side View.
Memory Usage: 21 MB, less than 28.81% of Swift online submissions for Binary Tree Right Side View.

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
