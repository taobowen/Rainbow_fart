&emsp;&emsp;���ı�����һ���ȽϾ�������⣬ͨ���ݹ�ķ�ʽ���Ժ����׵�д���������ǵݹ����ֶ�ջ��������⣬���Թ�����ͨ��Ҫ����д��Ҳ�Ƿǵݹ���㷨���ǵݹ��ʵ���޷Ǿ���ͨ��ջ�����е���ʽ��
**ǰ�����**
����һ��N�������������� ǰ�� ������

 ʾ��:

```
����:  
    1
  / | \
 2  3  4
  / | \
 5  6  7   

���: [1,2,3,5,6,7,4]
```

˼·��ջ

�ϴ��루js����
```
/**
 * // Definition for a Node.
 * function Node(val, children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */

/**
 * @param {Node} root
 * @return {number[]}
 */
var preorder = function(root) {
    if (!root) {
        return [];
    }

    let stack = [root],
        output = [];
    while (stack.length) {
        let outNode = stack.pop();
        output.push(outNode.val);
        if (outNode.children) {
            stack.push(...outNode.children.reverse());
        }
    }
    return output;
};
```

�ϴ��루python��:
```
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        if not root:
            return [];
        stack = [root];
        output = [];
        while len(stack):
            outNode = stack.pop();
            output.append(outNode.val);
            if outNode.children:
                stack = stack + list(reversed(outNode.children));
        return output;
```

**�������**
����һ��N�������������� ���� ������

ʾ��:

```
����:  
    1
  / | \
 2  3  4
  / | \
 5  6  7   

���: [2,5,6,7,3,4,1]
```
��ǰ������ĸ����Ҹ�Ϊ������Ȼ��ѱ������ȡ����

�ϴ��룺��js��
```
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */

/**
 * @param {Node} root
 * @return {number[]}
 */
var postorder = function(root) {
    let stack = [root],
        output = [];
    if (!root) {
        return output;
    }
    while (stack.length) {
        let outNode = stack.pop();
        output.push(outNode.val);
        if (outNode.children) {
            stack.push(...outNode.children);
        }
    }

    return output.reverse();
};
```

�ϴ��룺��python��

```
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        stack = [root];
        output = [];
        if not root:
            return output;

        while len(stack):
            outNode = stack.pop();
            output.append(outNode.val);
            if outNode.children:
                stack = stack + outNode.children;

        return list(reversed(output));
```

**�������**
����һ���������������������� ������

ʾ��:

```
����: [1,null,2,3]
   1
    \
     2
    /
   3

���: [1,3,2]
```

˼·��ջ

�ϴ��룺
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var inorderTraversal = function(root) {
    let stack = [],
        output = [];

    while (stack.length || root) {
        while (root && !root.isVisited) {
            stack.push(root);
            root.isVisited = true;
            root = root.left;
        }

        let outNode = stack.pop();
        output.push(outNode.val);
        root = outNode.right ? outNode.right : stack[stack.length - 1];
    }

    return output;
};
```

�ϴ��룺��python��
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        stack = []
        output = []
        while len(stack) or root:
            while root:
                stack.append(root)
                root = root.left

            outNode = stack.pop()
            output.append(outNode.val)
            root = outNode.right

        return output
```
