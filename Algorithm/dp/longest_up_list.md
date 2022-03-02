����һ��������������飬�ҵ���������������еĳ��ȡ�

**ʾ��:**

```
����: [10,9,2,5,3,7,101,18]
���: 4 
����: ��������������� [2,3,7,101]�����ĳ����� 4��
```
**˵��:**

���ܻ��ж�������������е���ϣ���ֻ��Ҫ�����Ӧ�ĳ��ȼ��ɡ�
���㷨��ʱ�临�Ӷ�Ӧ��Ϊ O(n2) ��
**����:** ���ܽ��㷨��ʱ�临�ӶȽ��͵� O(n log n) ��?
**˼·��** �������г�O��n2�����㷨����ʱ����¡�
**�ϴ��룺** 
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
    if(nums.length==0)
        return 0;
    var answer=[];
    for(let i=0;i<nums.length;i++){
        var max=-9999;
        answer[i]=1;
        for(let j=i-1;j>=0;j--){  
            if(nums[i]>nums[j]&&answer[j]>max){
                max=answer[j];
                answer[i]=answer[j]+1;
            }
        }
    }
    answer.sort(function(num1,num2){
        return num1-num2;
    });
    return answer[answer.length-1];
};
```