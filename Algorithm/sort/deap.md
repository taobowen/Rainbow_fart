![image](https://user-images.githubusercontent.com/46807600/58639185-09a1b080-8329-11e9-8c36-a1870ca3fb57.png)
![image](https://user-images.githubusercontent.com/46807600/58639239-2342f800-8329-11e9-9d51-3b3118d2e33d.png)

**���ڶѣ�** ����ͼ������һ����ȫ���������洢���������ʽ����ʱ���൱�ڶ�����������������⣬��������������ʱ��**�������������Ƿֱ�Ѷѷֳ�С���Ѻʹ󶥶�**��С���Ѿ��ǰѽ�С��Ԫ�ط��ڶѵĶ�������֮���󶥶Ѿ��ǰѽϴ��Ԫ�ط��ڶѵĶ��������Ҫ�ᵽ��һ���ǣ���������������ʽ�洢��ʱ��**�±�Ϊi�Ľ��������ӽڵ���±�ֱ�Ϊ2i+1��2i+2**��

**�㷨��⣺** 

������Ҫ�����϶����������������ܹ���Ϊ������

1. ����ʼ������ת��Ϊ�󶥶ѣ�heapify����ʵ���Ǵӵ�һ����Ҷ�ӽ�㿪ʼ��**���±� i = Math.floor(arr.length/2 - 1)** ���������ϣ��������󣬶�ÿһ����Ҷ�ӽ����shiftDown����������ʱ�����Ϊ���ֵ�����������һ����㽻����
2. �������һ����㣬������ڵ���ɵ��¶�ת��Ϊ�󶥶ѣ�����ֱ�ӶԸ��ڵ���shiftDown�����������ٸ��ڵ��λ�ü��ɣ�����ʱ�����Ϊ�����ֵ�����������һ����㽻����
3. �ظ�����2��ֱ������Ԫ�ظ���Ϊ1�������Ӧ����ĳ���Ϊ1����������ɡ�

**�ϴ��룺��js��**
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
function down (arr, startIndex, endIndex) {
    while (startIndex <= endIndex) {
        let childIndex = startIndex * 2 + 1;

        if (childIndex > endIndex) {
            return;
        }

        if (childIndex + 1 <= endIndex && arr[childIndex] < arr[childIndex + 1]) { // �󶥶�
            childIndex ++;
        }

        if (arr[childIndex] > arr[startIndex]) {
            [arr[startIndex], arr[childIndex]] = [arr[childIndex], arr[startIndex]];
        }

        startIndex = childIndex;
    }
}

var sortArray = function(nums) {
    for (let i = Math.floor(nums.length / 2 - 1); i >= 0; i --) {
        down(nums, i, nums.length - 1);
    }

    for (let i = 1; i <= nums.length; i++) {
        [nums[0], nums[nums.length - i]] = [nums[nums.length - i], nums[0]];
        down(nums, 0, nums.length - i - 1);
    }

    return nums;
};
```

**�ϴ��룺��python��**

```
import math;
class Solution:
    def down(self, arr: List[int], startIndex: int, endIndex: int):
        while startIndex < endIndex:
            childIndex = startIndex * 2 + 1;
            if childIndex > endIndex:
                return;
            if childIndex + 1 <= endIndex and arr[childIndex] < arr[childIndex + 1]:
                childIndex += 1;

            if arr[childIndex] > arr[startIndex]:
                arr[childIndex], arr[startIndex] = arr[startIndex], arr[childIndex];

            startIndex = childIndex;
    def sortArray(self, nums: List[int]) -> List[int]:
        for i in range(math.floor(len(nums) / 2 - 1), -1, -1):
            self.down(nums, i, len(nums) - 1);

        for i in range(1, len(nums)):
            nums[0], nums[len(nums) - i] = nums[len(nums) - i], nums[0];
            self.down(nums, 0, len(nums) - i - 1);

        return nums;
```