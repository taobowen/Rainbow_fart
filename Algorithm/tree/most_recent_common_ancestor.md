����һ��������, �ҵ�����������ָ���ڵ������������ȡ�

�ٶȰٿ�������������ȵĶ���Ϊ���������и��� T ��������� p��q������������ȱ�ʾΪһ����� x������ x �� p��q �������� x ����Ⱦ����ܴ�һ���ڵ�Ҳ���������Լ������ȣ�����

���磬�������¶�����:  root = [3,5,1,6,2,0,8,null,null,7,4]
![image](https://user-images.githubusercontent.com/46807600/58612589-b35f4e00-82e5-11e9-80ba-0a8dc011d2cb.png)
**ʾ�� 1:**
```
����: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
���: 3
����: �ڵ� 5 �ͽڵ� 1 ��������������ǽڵ� 3��
```
**ʾ�� 2:**
```
����: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
���: 5
����: �ڵ� 5 �ͽڵ� 4 ��������������ǽڵ� 5����Ϊ���ݶ�������������Ƚڵ����Ϊ�ڵ㱾��
```
 

**˵��:**

���нڵ��ֵ����Ψһ�ġ�
p��q Ϊ��ͬ�ڵ��Ҿ������ڸ����Ķ������С�

## ˼·
    ͨ��һ��ջʵ�ֵ�dfs�ֱ�õ��Ӹ��ڵ㵽Ŀ��ڵ��·����ע��Ҫ��һ��map��¼�Ѿ����ʹ��Ľڵ�
    �õ�����·����������˫ָ���ĩβ��ʼ������ֱ���ҵ���ͬ�ڵ㣬���ؼ���

## �ϴ��루js��
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
function findNodePath (root, node) {
    let stack = [],
        nodeMap = {};
    while (root || stack.length) {
        if (!nodeMap[root.val]) {
            stack.push(root);
            nodeMap[root.val] = true;
            if (root.val === node.val) {
                return stack;
            }
        }

        if (root.left && !nodeMap[root.left.val]) {
            root = root.left;
            continue;
        }

        if (root.right && !nodeMap[root.right.val]) {
            root = root.right;
            continue;
        }


        stack.pop();
        root = stack[stack.length - 1];
    }
}

var lowestCommonAncestor = function(root, p, q) {
    let pathP = findNodePath(root, p),
        pathQ = findNodePath(root, q),
        pathDiff = Math.abs(pathP.length - pathQ.length),
        pathPIndex,
        pathQIndex;

    if (pathQ.length > pathP.length) {
        pathQIndex = pathQ.length - 1 - pathDiff;
        pathPIndex = pathP.length - 1;
    } else {
        pathQIndex = pathQ.length - 1;
        pathPIndex = pathP.length - 1 - pathDiff;
    }

    while (true) {
        if (pathP[pathPIndex].val === pathQ[pathQIndex].val) {
            return pathP[pathPIndex];
        }
        pathPIndex --;
        pathQIndex --;
    }
};
```

## �ϴ��루python��
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def findNodePath (self, root, node) -> []:
        stack = [];
        nodeMap = {};
        while len(stack) != 0 or root:
            if not (root.val in nodeMap):
                nodeMap[root.val] = True;
                stack.append(root);
                if root.val == node.val:
                    return stack;

            if root.left and not (root.left.val in nodeMap):
                root = root.left;
                continue;

            if root.right and not (root.right.val in nodeMap):
                root = root.right;
                continue;

            stack.pop();
            root = stack[-1];

    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        pathP = self.findNodePath(root, p);
        pathQ = self.findNodePath(root, q);
        pathPIndex = pathQIndex = 0;
        pathDiff = abs(len(pathP) - len(pathQ));

        if len(pathP) > len(pathQ):
            pathPIndex = len(pathP) - 1 - pathDiff;
            pathQIndex = len(pathQ) - 1;
        else:
            pathPIndex = len(pathP) - 1;
            pathQIndex = len(pathQ) - 1 - pathDiff;

        while True:
            if pathP[pathPIndex].val == pathQ[pathQIndex].val:
                return pathP[pathPIndex];
            pathPIndex -= 1;
            pathQIndex -= 1;

```