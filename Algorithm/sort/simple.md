## ѡ������
### ˼�� 
&emsp;&emsp;���ȴ�ԭʼ�������ҵ���С��Ԫ�أ����Ѹ�Ԫ�ط����������ǰ�棬Ȼ���ٴ�ʣ�µ�Ԫ����Ѱ����С��Ԫ�أ�����֮ǰ��СԪ�صĺ��棬֪���������
### �ϴ��룺
```
function chooseSort(arr) {
    for(let i = 0; i < arr.length - 1; i++) {
        let minIndex = i;
        for(let j = i; j < arr.length; j++) {
            if(arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }
    return arr;
}
```
## ��������
### ˼��
&emsp;&emsp;��������Ĺ���ԭ����ǽ�δ�������ݣ����������������дӺ���ǰɨ�裬�ҵ���Ӧ��λ�ò����롣��������ͨ������ռλ����ʽ���ռ临�Ӷ�ΪO(1),��ˣ��ڴӺ���ǰɨ��Ĺ����У���Ҫ�����İ��������Ԫ�������Ųλ��Ϊ�²���Ԫ���ṩ�����λ�á�
### �ϴ��룺
```
function insertSort(arr) {
    for(let i = 0; i < arr.length; i++) {
        for(let j = 0; j < i; j++) {
            if(arr[j] > arr[i]) {
                let insertNum = arr[i];
                for(let k = i; k > j; k--) {
                    arr[k] = arr[k - 1];
                }
                arr[j] = insertNum;
                break;
            }
        }
    }
}
```
## ð������
### ˼��
&emsp;&emsp;�������� n �������Ƚ�ÿ���������������ǰ�ߴ��ں��ߣ��Ͱ�����������λ�ã�����һ������һ�־Ϳ���ѡ��һ����������������棻��ô���� n-1������� length - 1�� �֣��������������������
### �ϴ��룺
```
function bubleSort(arr) {
    for(let j = 0; j < arr.length - 1; j++) {
        for(let i = 0; i < arr.length - 1 - j; i++) {
            if(arr[i] > arr[i + 1]) {
                [arr[i], arr[i+1]] = [arr[i + 1], arr[i]];
            }
        }
    }
}
```