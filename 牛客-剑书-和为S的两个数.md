### [Question](https://www.nowcoder.com/practice/390da4f7a00f44bea7c2f3d19491311b?tpId=13&tqId=11195&tPage=3&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
```
function FindNumbersWithSum(array, sum)
{
    var res=[];
    if(array.length<2) return [];
    let start=0; let end=array.length-1;
    while(start<end){
        let temp=array[start]+array[end];
        if(temp<sum){
            start++;
        }
        if(temp>sum){
            end--;
        }
        if(temp == sum){
            return [array[start],array[end]];
        }
    }
    return [];
}
```

#### 两头乘积最小，所以两个指针，一个从头，一个从尾分别遍历，当第一次出现和为S时，乘积最小
