����һ�������������ĸ��ڵ� root ��һ��ֵ key��ɾ�������������е�?key?��Ӧ�Ľڵ㣬����֤���������������ʲ��䡣���ض������������п��ܱ����£��ĸ��ڵ�����á�

һ����˵��ɾ���ڵ�ɷ�Ϊ�������裺

�����ҵ���Ҫɾ���Ľڵ㣻
����ҵ��ˣ�ɾ������
˵���� Ҫ���㷨ʱ�临�Ӷ�Ϊ?O(h)��h Ϊ���ĸ߶ȡ�

ʾ��:

```
root = [5,3,6,2,4,null,7]
key = 3

    5
   / \
  3   6
 / \   \
2   4   7
```

������Ҫɾ���Ľڵ�ֵ�� 3���������������ҵ� 3 ����ڵ㣬Ȼ��ɾ������

һ����ȷ�Ĵ��� [5,4,6,2,null,null,7], ����ͼ��ʾ��

```
    5
   / \
  4   6
 /     \
2       7
```

��һ����ȷ���� [5,2,6,null,4,null,7]��

```
    5
   / \
  2   6
   \   \
    4   7
```
�ϴ��룺
```
var deleteNode = function(root, key) {
    if (!root){
        return root;
    }
    if (root.val > key){  //����ǰ���ֵ����ɾ��ֵ�����������������Ѱ��ɾ��ֵ
        root.left = deleteNode(root.left, key);
    }else if (root.val < key){  //����ǰ���ֵС��ɾ��ֵ�����������������Ѱ��ɾ��ֵ
        root.right = deleteNode(root.right, key);
    }else{  //�ҵ���ɾ������ȵĽ��
        if (root.left === null && root.right === null){  //Ҷ�ӽ��
            root = null;
        }else if (root.left === null){  //ֻ��������
            root = root.right;
        }else if (root.right === null){  //ֻ��������
            root = root.left;
        }else{  //ͬʱ������������
            let prevNode = root.left;
            while(prevNode.right){  //Ѱ�Ҳ����ڵ�ǰ���ֵ�������ֵ
                prevNode = prevNode.right;
            }
            root.val = prevNode.val;  //�滻ֵ
            root.left = deleteNode(root.left, prevNode.val);  //�ݹ���������ɾ���ظ�ֵ�Ľ��
        }
    } 
    return root;
};
```