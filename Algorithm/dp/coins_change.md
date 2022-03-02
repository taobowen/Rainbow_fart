������ͬ����Ӳ�� coins ��һ���ܽ�� amount����дһ��������������Դճ��ܽ����������ٵ�Ӳ�Ҹ��������û���κ�һ��Ӳ�����������ܽ����� -1��

**ʾ�� 1:**

```
����: coins = [1, 2, 5], amount = 11
���: 3 
����: 11 = 5 + 5 + 1
```
**ʾ�� 2:**

```
����: coins = [2], amount = 3
���: -1
```
**˵��:**
�������Ϊÿ��Ӳ�ҵ����������޵ġ�

**���** ������0/1�������⣬��ȡ�벻ȡ����dp��dfs��bfs���ֽⷨ������ֻ�г�dp�ġ���dp�������Ե����ϵķ�ʽȥ����
**�ϴ��룺**
```
/**
 * @param {number[]} coins
 * @param {number} amount
 * @return {number}
 */

var coinChange = function(coins, amount) {
    var answer=[0];
    for(let i=1;i<=amount;i++){
        answer[i]=amount+1;
        for(j in coins){
            if(i-coins[j]>=0){
                answer[i]=answer[i]>(answer[i-coins[j]]+1)?answer[i-coins[j]]+1:answer[i];
            }
        }
    }
    return answer[amount]==amount+1?-1:answer[amount]
};
```