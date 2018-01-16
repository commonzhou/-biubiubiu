## [Question](https://leetcode.com/problems/sliding-window-maximum/description/)
```c++
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        vector<int> slider;
        deque<int> maxwindow;
        if(nums.size()>=k && k>=1){
            for(int i=0;i<k;i++){
                while(!maxwindow.empty() && nums[i]>=nums[maxwindow.back()]){
                    maxwindow.pop_back();
                }
                maxwindow.push_back(i);
            }
            for(int i=k;i<nums.size();i++){
                slider.push_back(nums[maxwindow.front()]);
                while(!maxwindow.empty() && nums[i]>=nums[maxwindow.back()]){
                    maxwindow.pop_back();
                }
                if(!maxwindow.empty() && maxwindow.front()<=(i-k)){
                    maxwindow.pop_front();
                }
                maxwindow.push_back(i);
            }
            slider.push_back(nums[maxwindow.front()]);
        }
       return slider;
    }
};
```

#### 唉，此题剑书写的很好，我就是照着写的。需要使用deque这个双向队列，以及对应的一堆api。此题的秘诀在于，在队列里面存储最大的值，而且使得队列的第一个
#### 必为最大值（pop比入队小的数）！同时注意窗口移动使得队头要出队！这样队头是出，队尾除了进入还有出，所以使用deque，用queue就gg，好像list也可以。
