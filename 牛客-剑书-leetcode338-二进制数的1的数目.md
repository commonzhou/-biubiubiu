首先是`leetcode`的题目，关于二进制数字的1的数目。
其核心思想在于`i&(i-1)` 使得数字少一个1，从而来进行统计，这样的时间复杂度最低。换言之，把一个整数减去1，再和原整数进行与运算，会将整数的最右边的一个1变为0，
从而求出有多少个1。
## [Question](https://leetcode.com/problems/counting-bits/description/)
```javascript
/**
 * @param {number} num
 * @return {number[]}
 */
var countBits = function(num) {
    var result=[0];                     //第一个数字是0，1的位数也是0
    for(var i=1;i<=num;i++){
        var temp=result[i&(i-1)]+1;     //去掉最后一个1后的数，肯定比i自己小，
        result.push(temp);              //因此可以在数组里面找。找完加一，因为去掉了最后一个1。
    }
    return result;
};
```
另外，`i&(i-1)` 如果是0，说明i是2的幂。
上面这题，i是非负，再看看牛客（剑书）这题。i有负数的情况。本来也可以让数字不断右移来计数，但是正数右移左边补0，负数右移左边补一，因为负数的符号位是1，
而右移的空缺是按照符号位来补全的，这回使得负数出现死循环。所以还是用按位与的方法来做比较稳妥。
## [Question](https://www.nowcoder.net/practice/8ee967e43c2c4ec193b040ea7fbb10b8?tpId=13&tqId=11164&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
```javascript
function NumberOf1(n)
{
    var count=0;
    while(n){
      count++;
      n = n&(n-1);
    }
    return count;
}
```
