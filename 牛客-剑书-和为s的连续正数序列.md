### [Question](https://www.nowcoder.com/practice/c451a3fd84b64cb19485dad758a55ebe?tpId=13&tqId=11194&tPage=3&rp=3&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)
```
function FindContinuousSequence(sum)
{
   if(sum<=2) return[];
   let result=[];
   let a=1,b=2,s=3;
   while(a<=Math.floor(sum/2)){
       if(s<sum){
          b++;
          s+=b;
       }
       else if(s>sum){
          s-=a;
          a++;
       }
       else{
         let temp=[];
           for(let i=a;i<=b;i++){
              temp.push(i); 
           }
           result.push(temp);
           if(a+1<b){
               s-=a;
               a++;
           }
           else{
               break;
           }
       }
   }
   return result;
}
```

*  设定两个指针，如果和大于sum，左指针向后移位，如果小于，右指针向后移位。 如果两个指针碰在一起，则跳出，左指针一直小于sum的一半。
