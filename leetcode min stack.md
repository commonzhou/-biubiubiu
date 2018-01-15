## [Question](https://leetcode.com/problems/min-stack/description/)
```C++
class MinStack {
public:
    /** initialize your data structure here. */
    struct ListNode{
         int val;
         ListNode* next;
         ListNode(int x):val(x),next(NULL){}
       };
    ListNode* headnode;
    ListNode* minhead;
    
    int min;
    MinStack() {
       headnode= new ListNode(0);
       minhead = new ListNode(0);
    }
    
    void push(int x) {
       
       if(headnode->next == NULL){min=x;}                
       else{
           min= (min>x)?x:min;                        切记要先比较大小啊！然后再添加节点，否则傻了吧
       } 
       
       ListNode* pushNode=new ListNode(x); 
       ListNode* temp=headnode->next;
       headnode->next=pushNode;
       pushNode->next=temp;
        
      
       ListNode* minnode=new ListNode(min);
       ListNode* mintemp=minhead->next;
       minhead->next=minnode;
       minnode->next=mintemp;    
    }
    
    void pop() {
       if(headnode->next == NULL){
           printf("stack is empty!!!\n");
       }
       else{
           ListNode* temp=headnode->next;
           headnode->next=headnode->next->next;
           free(temp);
           temp=NULL;
           
           ListNode* mintemp=minhead->next;
           minhead->next=minhead->next->next;
           free(mintemp);
           mintemp=NULL;
           if(minhead->next  != NULL){             
               min=minhead->next->val; 
               //此处需要更新最小值min，切记
          }
       } 
    }
    
    int top() {
        if(headnode->next==NULL){printf("stack is empty!!!\n");}
        else{
          ListNode* temp=headnode->next;
          return temp->val;   
        }  
    }
    
    int getMin() {
        if(headnode->next==NULL){printf("stack is empty!!!\n");}
        else{
          return minhead->next->val;  
        }  
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```
## 额，虽然长，但是很全面。首先是使用链表实现了栈的结构，每次都往表头添加节点。然后注意栈的判空。最大的亮点的对于最小值的处理，使用一个辅助栈来进行存储，很神奇，注意点是当有节点出栈时，对于全局的最小值min，要进行更新，便于以后进行比较。
