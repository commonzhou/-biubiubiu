### [Question](https://leetcode.com/problems/rotate-list/description/)
``` c++
class Solution {
 public:
    ListNode* rotateRight(ListNode* head, int k) {
        if(head==NULL || k==0) return head;
        ListNode* headnode=new ListNode(0);
        headnode->next=head;
        ListNode* temp1=headnode; ListNode*temp2=head;int n1=0,n2=0;
        while(temp1->next!=NULL){
            n1++;
            temp1=temp1->next;
        }
       
        if(n1<=k) {
            k=k%n1;
            if(k==0) {return head;}
        }
            
            while( (n2+k+1)<n1 ){
                temp2=temp2->next;
                n2++;
            }
            ListNode* temp3=temp2->next;
            temp2->next=NULL;
            temp1->next=head;
            return temp3;
    
    }
};
```

#### 难点在于k比链表长度大时，需要对于k%n给k，此时k==0就返回head，其他还好。另外经童书提醒，可以快慢指针，快者先到达第k个，
#### 然后慢指针从头出发，快的到结尾时，慢指针应该离结尾k个
