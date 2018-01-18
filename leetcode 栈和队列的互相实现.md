### 这次两道题目一起更新，分别是[用栈实现队列](https://leetcode.com/problems/implement-stack-using-queues/description/) 和[用队列实现栈](https://leetcode.com/problems/implement-queue-using-stacks/description/)
#### 首先是栈实现队列，两栈实现一个队列，核心是将一个栈pop出来push到另一个栈，刚好逆序啊，完美！
#### 不过stack的pop返回空，需要使用top来获得出栈的数字

```c++
class MyQueue {
public:
    /** Initialize your data structure here. */
    stack<int>stack1;
    stack<int>stack2;
    MyQueue() {
        
    }
    
    /** Push element x to the back of queue. */
    void push(int x) {
        stack1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    int pop() {
        if(stack2.empty()){
           while(!stack1.empty()){
               int temp=stack1.top();
               stack1.pop();
               stack2.push(temp);
           } 
        }
        int popvalue = stack2.top();
        stack2.pop();
        return popvalue;
    }
    
    /** Get the front element. */
    int peek() {
       if(stack2.empty()){
          while(!stack1.empty()){
              int temp=stack1.top();
              stack1.pop();
              stack2.push(temp);
          } 
       } 
       return stack2.top();
    }
    
    /** Returns whether the queue is empty. */
    bool empty() {
        if(stack1.empty() && stack2.empty()){
            return true;
        }
        else{
            return false;
        }
    }
};
```

#### 然后是队列实现栈,两个队列互相倒来倒去就好，重点是队列方法的使用，比如队列的back方法，是模仿栈的top方法的利器。
#### 另外，discuss里面有用[一个队列](https://leetcode.com/problems/implement-stack-using-queues/discuss/62527)的方法，惊艳全场，核心思想是队列的存储顺序，每push一个数字，就将队列里面数字的顺序逆序一次，这样pop出来的数，就是栈应该pop出来的数。
```c++
class MyStack {
public:
    /** Initialize your data structure here. */
    queue<int>queue1;
    queue<int>queue2;
    MyStack() {
        
    }
    
    /** Push element x onto stack. */
    void push(int x) {
        if(queue1.empty()){
            queue2.push(x);
        }
        else{
            queue1.push(x);
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        if(queue1.empty()){
           while(queue2.size() !=1){
               queue1.push(queue2.front());
               queue2.pop();
           } 
           int temp=queue2.front(); 
           queue2.pop();
           return temp;
        }
        else{
           while(queue1.size() !=1){
             queue2.push(queue1.front());
             queue1.pop();
           } 
           int temp=queue1.front();
           queue1.pop();
           return temp;
        }
    }
    
    /** Get the top element. */
    int top() {
        if(queue1.empty()){
           return queue2.back(); 
        }
        else{
           return queue1.back(); 
        } 
    }
    
    /** Returns whether the stack is empty. */
    bool empty() {
        if(queue1.empty() && queue2.empty()){
            return true;
        }
        else{return false;}
    }
};
```
