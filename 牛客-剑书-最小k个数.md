### [Question](https://www.nowcoder.com/practice/6a296eb82cf844ca8539b57c23e6e9bf?tpId=13&tqId=11182&tPage=2&rp=2&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
```
function GetLeastNumbers_Solution(input, k)
{
   let result=quickSort(input);
   if(result.length<k) return [];
   else{
      return result.slice(0,k);  
    }
}

function quickSort(data){
    if(data.length<2) return data;
    let pivotIndex=Math.floor(data.length/2);
    let pivot=data.splice(pivotIndex,1)[0];
    let left=[];let right=[];
    for(let i=0;i<data.length;i++){
        if(data[i]<pivot){
            left.push(data[i]);
        }
        else{
           right.push(data[i]);
        }
    }
    return quickSort(left).concat([pivot],quickSort(right));
}
```

#####  直接上了快排。另外，如果是C++的话，可以借助partition函数来做，不过js咋写我就不知道了。。。还有就是最大堆可以在这里应用，参见剑指offer。
#####  大意是辅助数组k这么大，求出其中最大的值（使用最大值），每次都是从原数组取一个数和这个辅助数组的最大值比，如果小就和最大值替换，重新求出辅助
#####  数组的最大值。。。如此的好处是，不用修改原来的数组，适合大数据处理。
#####  不过更扎心的是，js的sort内部实现，大致是个数小于22使用插入排序，大于22使用快排。。。。。。。
