## ˼��
&emsp;&emsp;������������������Сʱ�ر��Ч�������˼�����˫ָ�룬����tagIndexȡֵ�Ĳ�ͬ���Ȼ���ָ�뻹����ָ�����Ҫ

## �ϴ��룺��js��
### ȡ����Ԫ����Ϊ������
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */

var sortArray = function(nums) {
    let stack = [{
        left: 0,
        right: nums.length - 1
    }];

    while (stack.length) {
        let {left, right} = stack.pop();
        if (left >= right) {
            continue;
        }

        let markIndex = left,
            leftIndex = left,
            rightIndex = right;
        while (leftIndex < rightIndex) {
            while (nums[rightIndex] >= nums[markIndex] && rightIndex > leftIndex) {
                rightIndex --;
            }

            while (nums[leftIndex] <= nums[markIndex] && leftIndex < rightIndex) {
                leftIndex ++;
            }

            [nums[leftIndex], nums[rightIndex]] = [nums[rightIndex], nums[leftIndex]];
        }

        [nums[markIndex], nums[leftIndex]] = [nums[leftIndex], nums[markIndex]];
        stack.push({
            left,
            right: leftIndex - 1
        }, {
            left: rightIndex + 1,
            right
        })
    }

    return nums;
};
```

## �ϴ��룺��python��
```
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        stack = [{
            'left': 0,
            'right': len(nums) - 1
        }];
        while len(stack):
            outList = stack.pop();
            leftIndex = outList['left'];
            rightIndex = outList['right'];
            tagIndex = leftIndex;
            if leftIndex >= rightIndex:
                continue;

            while leftIndex < rightIndex:
               
                while nums[rightIndex] >= nums[tagIndex] and rightIndex > leftIndex:
                    rightIndex -= 1;

                while nums[leftIndex] <= nums[tagIndex] and rightIndex > leftIndex:
                    leftIndex += 1;

                nums[leftIndex], nums[rightIndex] = nums[rightIndex], nums[leftIndex];
            
            nums[tagIndex], nums[rightIndex] = nums[rightIndex], nums[tagIndex];
            
            stack.extend([{
                'left': outList['left'],
                'right': leftIndex - 1
            }, {
                'left': leftIndex + 1,
                'right': outList['right']
            }]);
            
        return nums;
```
