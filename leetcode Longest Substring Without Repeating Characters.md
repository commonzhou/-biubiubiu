
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
* 另一种常见的套路是，字典！ vector<int> dictionary(256,-1);  256个-1，喵的因为扩展后的ASCII码是256个。。。
  然后遍历字符串，每次进入一个字符就查阅字典，若字典里没有就记录下字符在串里的位置。若字典里面有，就更新start的位置。从而不断计算
  maxlength，直到遍历完成。。
  代码如下：
```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int> temp(256,-1);
        int maxlength=0,start=-1;
        for(int i=0;i<s.size();i++){
            if(temp[s[i]]>start){
                start=temp[s[i]];
            }
            temp[s[i]]=i;
            maxlength=max(maxlength,i-start);
        }
        return maxlength;
    }
};
```
