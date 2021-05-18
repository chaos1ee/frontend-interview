# BFS

给定一棵二叉树，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。

示例:

输入: [1,2,3,null,5,null,4]
输出: [1, 3, 4]
解释:

```
 1 <---
/ \
2 3 <---
 \ \
  5 4 <---
```

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var rightSideView = function (root) {
  if (!root) return [];

  const ret = [];
  const queue = [root];

  while (queue.length > 0) {
    let len = queue.length;

    while (len) {
      const node = queue.shift();

      if (len === 1) ret.push(node.val);
      if (node.left) queue.push(node.lef);
      if (node.right) queue.push(node.right);

      len--;
    }
  }
  return ret;
};
```
