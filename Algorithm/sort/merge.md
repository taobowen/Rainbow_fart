### ˼��
&emsp;&emsp;����һ�ַ����㷨����ԭʼ�����зֳɽ�С�����飬ֱ��ÿ��С����ֻ��һ�Ȼ���ڽ�С����鲢Ϊ�ź���Ľϴ����飬ֱ�����õ�һ���ź����������顣

### �ϴ��룺(js)
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */

function mergeArr (arr1, arr2) {
    let output = [],
        index1 = 0,
        index2 = 0;

    while (index1 < arr1.length && index2 < arr2.length) {
        if (arr1[index1] < arr2[index2]) {
            output.push(arr1[index1]);
            index1 ++;
        } else {
            output.push(arr2[index2]);
            index2 ++;
        }
    }

    if (index1 < arr1.length) {
        output.push(...arr1.slice(index1));
    } else if (index2 < arr2.length) {
        output.push(...arr2.slice(index2));
    }

    return output;
}

var sortArray = function(nums) {
    if (nums.length <= 1) {
        return nums;
    }

    let midIndex = Math.floor(nums.length / 2),
        leftArr = sortArray(nums.slice(0, midIndex)),
        rightArr = sortArray(nums.slice(midIndex));

    return mergeArr(leftArr, rightArr);
};
```

### �ϴ��룺(python)

```
import math;

class Solution:
    def mergeArr(self, leftArr, rightArr) -> List[int]:
        output = [];
        leftIndex = rightIndex = 0;
        while leftIndex < len(leftArr) and rightIndex < len(rightArr):
            if leftArr[leftIndex] < rightArr[rightIndex]:
                output.append(leftArr[leftIndex]);
                leftIndex += 1;
            else:
                output.append(rightArr[rightIndex]);
                rightIndex += 1;

        if leftIndex < len(leftArr):
            output += leftArr[leftIndex:];
        elif rightIndex < len(rightArr):
            output += rightArr[rightIndex:];

        return output;
        
    def sortArray(self, nums: List[int]) -> List[int]:
        if len(nums) <= 1:
            return nums;
        midIndex = math.floor(len(nums) / 2);
        leftArr = self.sortArray(nums[:midIndex]);
        rightArr = self.sortArray(nums[midIndex:]);

        return self.mergeArr(leftArr, rightArr);
       
```