�� O(n log n) ʱ�临�ӶȺͳ������ռ临�Ӷ��£��������������

ʾ�� 1:

```
����: 4->2->1->3
���: 1->2->3->4
```
ʾ�� 2:

```
����: -1->5->3->4->0
���: -1->0->3->4->5
```
��������õ��ǹ鲢���򣬺�����Ĺ鲢����֮ͬ������Ҫͨ������ָ��Ѱ�ҵ��м�ڵ㣬����merge�������ڲ��������ռ������ºϲ����������������������Ҳ��Щ��ͬ����֮������������Ƕ������㷨�����������һ���ۺϿ��죬�������£�
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var merge=function(l,r){
    let last={};
    let head=last;
    while(l||r){
        if(r&&(!l||l.val>r.val)){
            last.next=r;
            last=last.next;
            r=r.next;
        }else{
            last.next=l;
            last=last.next;
            l=l.next;
        }
    }
    return head.next;
}
var sortList = function(head) {
    if(!head||head.next==null){
        return head;
    }
    let f=head;
    let s=head;
    let last;
    while(f.next!=null){
        f=f.next.next;
        last=s;
        s=s.next;
        if(!f){
            break;
        }
    }
    last.next=null;
    let left=sortList(head);
    let right=sortList(s);
    return merge(left,right);
};
```