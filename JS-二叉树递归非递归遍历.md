#### 首先，测试用的树如下
```
var root={
	val:1,
	left:{
		val:2,
		left:{val:4},
		right:{val:5}
	},
	right:{
		val:3,
		left:{val:6},
		right:{val:7}
	}
}
```
#### 递归的三种，先序中序后序
```
//  先序
function MLR(root){
	if(root!=null){
		console.log(root.val);
		MLR(root.left);
		MLR(root.right);
	}	
}

// 中序
function LMR(root){
	if(root!=null){
		LMR(root.left);
		console.log(root.val);
		LMR(root.right);
	}	
}

// 后序
function LRM(root){
	if(root!=null){
		LRM(root.left);
		LRM(root.right);
		console.log(root.val);
	}	
}
```

#### 重头戏来了。非递归怎么搞？
```
// 先序
function MLR(root){
	var arr=[],res=[];
	if(root!=null){
	  arr.push(root);
	}	
	while(arr.length){
	   var temp=arr.pop();
	   res.push(temp.val);
	   if(temp.right!=null) arr.push(temp.right);
	   if(temp.left!=null)  arr.push(temp.left);
	   // 先右后左，因为取出来的顺序相反
	}
	return res;
}

// 中序
function LMR(root){
	var arr=[],res=[];
	while(true){           //先将左节点依次放入
	  while(root!=null){
		  arr.push(root);
		  root=root.left;
	  }
	// 终结条件，遍历完成
	if(arr.length==0){
		break;
	}
	var temp=arr.pop();
	res.push(temp.val);  
	root=temp.right;     //左中右顺序
	}
	return res;
}

// 后序
function LRM(root){
	var arr=[],res=[];
	arr.push(root);
    while(arr.length!=0){
	  var temp=arr.pop();
	  res.push(temp.val);
	  if(temp.left) {arr.push(temp.left);}
	  if(temp.right){arr.push(temp.right);}
	}
	// 此时res的排序是中右左
	return res.reverse();
}
```
#### 总结一下，前后相仿，只不过读的时候顺序不同，后序还逆序了一下；中序一路先读左边，然后左中右这样的输出
