����һ��δ������������飬�ҳ���������еĳ��ȡ�

Ҫ���㷨��ʱ�临�Ӷ�Ϊ O(n)��

**ʾ��:**
```
����: [100, 4, 200, 1, 3, 2]
���: 4
����: ����������� [1, 2, 3, 4]�����ĳ���Ϊ 4��
```
**˼·��** һ�����������У������������ϵ��������������뵽����ͨ�������ֵ�ķ�ʽ����¼�������ֵķ���״̬���������ؼ���һ������ô�����������б仯��״̬����������������ֵ��Ϊ�ֵ�������������������У�����ֻ�������е����˼�¼���г���ÿ����һ�����֣��͸����ֵ��������������˵ĳ���ֵ��
**�ϴ��룺**
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var longestConsecutive = function(nums) {
    var max=0;
    var dic=[];//�ֵ�
    for(i in nums){
        let left=0;
        let right=0;
        if(!isNaN(dic[nums[i]])){
            continue;
        }
        if(!isNaN(dic[nums[i]-1])){
            left=dic[nums[i]-1];
        }
        if(!isNaN(dic[nums[i]+1])){
            right=dic[nums[i]+1];
        }
        dic[nums[i]]=1+left+right;
        max=max<dic[nums[i]]?dic[nums[i]]:max;
        dic[nums[i]-left]=left+right+1;
        dic[nums[i]+right]=right+left+1;
    }
    return max;
};
```