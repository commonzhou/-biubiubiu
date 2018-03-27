### [Question](https://leetcode.com/problems/multiply-strings/description/)
```
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var multiply = function(num1, num2) {
    if(num1==0||num2==0) return '0';
    var arr1=num1.split('').reverse();
    var arr2=num2.split('').reverse();
    var len1=arr1.length;
    var len2=arr2.length;
    
    var result=[];
    for(var i=0;i<len1;i++){
        for(var j=0;j<len2;j++){
            result[i+j]=0;
        }
    }
    for(var i=0;i<len1;i++){
       for(var j=0;j<len2;j++){
         result[i+j]+=parseInt(arr1[i])*parseInt(arr2[j]);
       }
    }
 
    var len=result.length;
    result[len]=0;
    for(var k=0;k<len;k++){
       if(result[k]>=10){
           var temp=result[k];
           result[k]=temp%10;
           result[k+1]+=Math.floor(temp/10);
       }
    }
    if(result[result.length-1]==0){
       result.pop();
    }
    var returnValue=result.reverse().join('');
    return returnValue;
};
```
##### 此题需要将大数看为字符串，逆序来进行乘法，result[i+j]+=parseInt(arr1[i])*parseInt(arr2[j]); 这一步是核心啊



