## [Question](https://leetcode.com/problems/valid-parentheses/description/)
```C++
class Solution {
public:
    bool isValid(string s) {
        stack<char>temp;
        for(auto i : s){
           switch(i){
               case '('  :  temp.push(i); break;
               case '{'  :  temp.push(i); break;
               case '['  :  temp.push(i); break;
               case ')'  :  if(temp.empty() || temp.top()!='(') {return false;}  
                            temp.pop();
                            break;
               case '}'  :  if(temp.empty() || temp.top()!='{') {return false;}  
                            temp.pop();
                            break;
               case ']'  :  if(temp.empty() || temp.top()!='[') {return false;}
                            temp.pop();
                            break;
               default:break;
           } 
        }
        if(temp.empty()){return true;}
        else{
            return false;
        }
        //此处可以写为 return temp.empty();
    }
};
```

#### 此题使用了stack这个模板，以及for和switch等基本用法，主要是使用栈来存储符号并比较的思想，注意两种特殊情况，一是栈最后不为空，比如剩下[
#### 另一个是输入只有]这种情况，此时原来栈是空的，pop不了东西，二者皆false
