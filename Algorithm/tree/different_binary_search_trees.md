## ���
����һ������ n������������ 1 ... n Ϊ�ڵ�����ɵ� ���������� 
## ˼·
�鲢���򣬵���Ҫ�������еĶ������������ڴ�ͳ�Ĺ鲢��Ҫ�޸�һ�£�middle����hard֮����Ѷȣ������˹鲢Ӧ�ò��ѣ���Ҫ��������Ҫ�󷵻ص����ݽṹ�Ͷ����ı�����ʽ�е���

�ϴ���
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
 * @param {number} n
 * @return {TreeNode[]}
 */
function buildBinaryTree (start, end, arr) {
    let output = [];
    if (start >= end) {
        return [[null]];
    }

    for (let i = start; i < end; i++) {
        output.push(...mergeTree(buildBinaryTree(start, i, arr), arr[i], buildBinaryTree(i + 1, end, arr))); 
    }

    return output;
}

function mergeTree (leftTree, rootVal, rightTree) {
    let output = [];

    for (let i = 0;i < leftTree.length; i++) {
        for (let j = 0; j < rightTree.length; j++) {
            output.push([new TreeNode(rootVal, leftTree[i][0], rightTree[j][0]), ...leftTree[i], ...rightTree[j]]);
        }
    }
    return output;
}

var generateTrees = function(n) {
    let baseArr = [];

    for (let i = 1; i <= n; i++) {
        baseArr.push(i);
    }

    return buildBinaryTree(0, n, baseArr).map(item => item[0]);
};
```