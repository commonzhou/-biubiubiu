### [Question](https://leetcode.com/problems/linked-list-cycle-ii/description/)
```c++
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode* slow=head;
        ListNode* fast=head;
        ListNode* slow2=head;
        if(head==NULL){return NULL;}
        if(head->next == NULL){return NULL;}
        while(fast!=NULL && fast->next!=NULL){
            slow=slow->next;
            fast=fast->next->next;
            if(slow==fast){
                while(slow !=slow2){
                    slow=slow->next;
                    slow2=slow2->next;
                }
                return slow2;
            }
        }
        return NULL;
    }
};
```

#### 链表有环时，有一个数学推导，证明慢1从快慢相遇点出发，慢2从链表头出发，二者相遇在环的入口。
     2s=s+nr, s=nr=(n-1)r+r=(n-1)r+L-x
     s=L-y, x=(n-1)r+y
     其中，s为慢1在快慢相遇时所走距离，n为圈数，r为一圈环的长度，x为链表起点到环入口的距离，y为快慢相遇点到环入口的距离
     
     
