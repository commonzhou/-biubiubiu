#### [Question](https://www.nowcoder.com/practice/529d3ae5a407492994ad2a246518148a?tpId=13&tqId=11167&tPage=1&rp=2&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
```
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/

function FindKthToTail(head, k)
{
   if(!head || (k<=0)) return null;
   var s1=head; var s2=head;
   for(var i=0;i<k-1;i++){               // 倒数第k个，走k-1步哦
       if(s2.next!=null){
           s2=s2.next;
       }
       else{
           return null;
       }
    }
    while(s2.next!=null){
        s1=s1.next;
        s2=s2.next;
    }
    return s1;
}
```
####  使用快慢指针
