## ����
�����ѧ�ڱ���ѡ�� numCourses �ſγ̣���Ϊ?0?��?numCourses - 1 ��

��ѡ��ĳЩ�γ�֮ǰ��ҪһЩ���޿γ̡� ���޿γ̰�����?prerequisites ����������?prerequisites[i] = [ai, bi] ����ʾ���Ҫѧϰ�γ�?ai �� ���� ��ѧϰ�γ�? bi ��

���磬���޿γ̶�?[0, 1] ��ʾ����Ҫѧϰ�γ� 0 ������Ҫ����ɿγ� 1 ��
�����ж��Ƿ����������пγ̵�ѧϰ��������ԣ����� true �����򣬷��� false ��
## ˼·

�������BFS��DFS���ַ�����

### BFS

�������У����ȱ���ͼ���ҵ��������Ϊ0�Ľڵ㣬��ӣ�
Ȼ��ѭ���������������нڵ�

- ���Ϊ0�����ӣ������ӽڵ㣬�����ӽڵ���ȼ�һ��֮���ٽ����Ϊ0���ӽڵ���ӡ�
- ��Ȳ�Ϊ0�����ڵ��Ƶ�����ĩβ

ֱ������Ϊ��
��Ϊ���е����нڵ���ô������ȶ�������0������ڴ��ڼ���ӽڵ�������ͼ���ܽ������ȣ���˵��ͼ���޻���

### �ϴ���
```
function Node (val) {
    this.val = val;
    this.pre = 0;
    this.neighbors = [];
}

var canFinish = function(numCourses, prerequisites) {
    let allNodeMap = [],
        queue = [],
        effectiveCourse = 0;

    prerequisites.forEach((item, index) => {
        if (!allNodeMap[item[0]]) {
            allNodeMap[item[0]] = new Node(item[0]);
        }

        if (!allNodeMap[item[1]]) {
            allNodeMap[item[1]] = new Node(item[1]);
        }

        allNodeMap[item[1]].pre ++;

        allNodeMap[item[0]].neighbors.push(allNodeMap[item[1]]);
    });

    for (let i = 0; i < numCourses; i ++) {
        if (!allNodeMap[i]) {
            effectiveCourse ++;
            continue;
        }

        if (allNodeMap[i].pre === 0) {
            queue.push(allNodeMap[i]);
        }
    }

    while (queue.length) {
        let outNode = queue.shift();
        if (outNode.pre === 0) {
            outNode.neighbors.forEach(item => {
                item.pre --;
                if (item.pre === 0) {
                    queue.push(item);
                }
            });
            effectiveCourse ++;
            continue;
        }

        queue.push(outNode);
    }

    return effectiveCourse === numCourses;
};
```