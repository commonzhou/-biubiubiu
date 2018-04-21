### [Question](https://www.nowcoder.com/practice/ef068f602dde4d28aab2b210e859150a?tpId=13&tqId=11215&tPage=4&rp=3&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)
```
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */

/*function KthNode(pRoot, k)
{
    var arr=[],res=[];
    while(true){           //先将左节点依次放入
	  while(pRoot!==null){
		  arr.push(pRoot);
		  pRoot=pRoot.left;
	  }
	// 终结条件，遍历完成
	if(arr.length===0){
		break;
	}
	var temp=arr.pop();
	res.push(temp.val);  
	pRoot=temp.right;     //左中右顺序
	}
    
    if(res.length < k || k < 1) return null;
    else{
        return res[k-1];
    }
}*/

function KthNode(pRoot, k)
{
    var arr=[];
    if(pRoot===null||k<1){
        return null;
    }
    function midInorder(root){
        if(root.left!==null){
             midInorder(root.left);
        }
        arr.push(root);
        if(root.right!==null){
            midInorder(root.right);
        }
    }
    midInorder(pRoot);
    return arr[k-1];
}
```

####   一直想不通，为啥非递归的过不了。。。。有啥子区别哦
