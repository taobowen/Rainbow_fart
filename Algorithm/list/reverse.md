��תһ��������

ʾ��:

```
����: 1->2->3->4->5->NULL
���: 5->4->3->2->1->NULL
```

��ת�����е����͵ݹ����ַ�ʽ���������ȷ��ϵ����ķ�ʽ��˼·���ȴ���һ���յ�ͷ���ָ��ԭ��������ͷ��Ȼ����������ѵ�ǰ������뵽�յ�ͷ���󣬴������£�
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
var reverseList = function(head) {
    if(!head||!head.next){
        return head;
    }
    var f=head.next;
    var s=head;
    var dummy=new ListNode();
    dummy.next=head;
    while(f){
        s.next=f.next;
        f.next=dummy.next;
        dummy.next=f;
        f=s.next;
    }
    return dummy.next;
};
```