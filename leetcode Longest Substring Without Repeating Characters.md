## [Question](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        string temp;
        int maxlength=0; 
        for(auto c : s){
            if(temp.empty()){
                temp+=c;
            }
            else{
               if(temp.find(c) == string::npos){
                   temp+=c;
               } 
                else{
                    if(temp.size() > maxlength){maxlength=temp.size();}
                    temp = temp.substr( temp.find(c) + 1 );
                    temp.append(1,c);
                }
            }
        }
        if(temp.size() > maxlength){maxlength=temp.size();}        //针对 "abc" 或者 "aabc"这类情况
        return maxlength;
    }
};
```

#### 小结
* 新建字符串temp，往里面加入字符c，每次在temp里面find字符c，如果重复了，从find的地方往后substr，继续加入字符，找最大长度
