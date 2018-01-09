### [Question](https://leetcode.com/problems/linked-list-cycle/description/)
```C++
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* fast=head;
        ListNode* slow=head;
        if(fast==NULL) return false;
        else if(fast->next==NULL)return false;
        else{
            while(fast!=NULL && fast->next!=NULL){
                slow=slow->next;
                fast=fast->next->next;
                if(fast==slow){return true;}
            }
            return false;
        }
    }
};
```

#### 链表找环，使用快慢指针，若有环，二者必将相遇，此乃套路也
