# DFS

## #1

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 * 深度优先dfs结合回溯
 * 递归节点以实现深度优先遍历
 * 确定回溯条件：path.length === 3 && sum(path) === 0
 * 注意path.slice()，直接传path因为是引用的关系会出错
 */
var threeSum = function (nums) {
  const res = [];
  const used = {};
  const picked = {};
  const arr = nums.slice();

  const depth = 3;

  function dfs(path) {
    if (path.length === depth && sum(path) === 0) {
      const key = path.slice().sort().join("_");
      if (!picked[key]) {
        res.push(path.slice());
        picked[key] = true;
      }
      return;
    }

    for (let i = 0; i < arr.length; i++) {
      if (used[i]) continue;
      path.push(arr[i]);
      used[i] = true;
      dfs(path);
      path.pop();
      used[i] = false;
    }
  }

  dfs([]);
  return res;
};

function sum(arr) {
  return arr.reduce((acc, curr) => {
    acc += curr;
    return acc;
  }, 0);
}
```

## #2

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
  const res = [];

  function dfs(root, step, res) {
    if (root) {
      if (res.length === step) {
        res.push(root.val);
      }

      dfs(root.right, step + 1, res);
      dfs(root.left, step + 1, res);
    }
  }

  dfs(root, 0, res);

  return res;
};
```
