### [Question](https://www.nowcoder.com/practice/7a0da8fc483247ff8800059e12d7caf1?tpId=13&tqId=11200&tPage=3&rp=3&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
```javascript
function Sum_Solution(n)
{
    let sum=n;
    let ifTermination=(n!=0)&&(sum+=Sum_Solution(n-1));    //&&的短路运算，很神奇！！NB
    return sum;
}
```

##### 求1到n的和，相当巧妙的算法思想啊，利用了&&的短路原理，令人叹服。。。
