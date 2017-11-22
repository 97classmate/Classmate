##1、%(取摸)的应用
```
<script>
   window.onload=function ()
{  
     var  aLi=document.getElemetsByTagName('li');
       for(var i=0;i<aLi.length;i++)
{
               // i 0 1 2 3 4 5 6
              if (i%2==0)
            {
                   aLi[i].style.background='#yellow';
             }
              else                //隔行变色的效果
             }
                         aLi[i].style.background=' ';
             }
}
</                        script>
```
##2、秒转时间例子
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Wang.qingwen</title>
	<script >

	//秒转时间的例子，一一般用再抢购等倒计时上！
		var s =1314520;
		alert(parseInt(s/60)+'分'+s%60+'秒');
	</script>
</head>
<body>
	
</body>
</html>
```
##3、arguments用法
  - 是个数组，多少参都可以。
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Wang.qingwen</title>
	<script >
       function sum()
       {
       	var resultt=0;
       	for (var i=0;i<arguments.length;i++)
       	{
       		resultt+=arguments[i];//循环把每个数值相加
       	}
       	return resultt;
       }
       alert(sum(1314520,3245,465,56,52,1,2,52,1));
	</script>
</head>
<body>
	
</body>
</html>
```

##4、获取非行间元素
- 该代码好像失效
    
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Wang.qingwen</title>
	<style >
		#divl {width:200px;height: 20px;background: #000000;}
	</style>
	<script >
function getStyle(obj,name)
{
     if (obj.currentStyle)//判断浏览器兼容
       	{
       		return obj.currentStyle[name];
       	}
       	else
       	{
       		return getComputedStyle(obj,false)[name];
       	}
}
       window.onload= function ()
       {
       	var oDiv=document.getElementByID('divl');

       	alert(getStyle(oDiv,'width'));
       };
	</script>
</head>
<body>
	
</body>
</html>

```
##5、数组添加和删除元素
   - 添加
           (1)push，从尾部添加
           (2)unshift, 从头部添加
- 删除
          (1)pop,从尾部删除
          (2)shift ,从头部删除
- 插入、删除
     (1)splice(开始，长度，元素....)
      先删除，后插入
     (2)删除
            splice(开始，长度)
      (3)插入
             splice(开始，0，元素....)
- 排序、转换
         排序
            (1)sort([比较函数])，排序一个数组   
         转换
    (2)concat(数组2) ，连接两个数组
    (3)join(分隔符)，用什么代表分隔符都可以
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>例子</title>
	
	<script >
        var love=[1,2,3];
             love.push(2);
        alert(love);
	</script>
</head>
<body>
	
</body>
</html>
```

#二0、DOM基础
 - 创建DOM元素
 1.createElement(标签名) 作用是 创建一个子节点。
2.appendChild(节点) 追加一个子节点，下面来看代码。
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
     	var oBtn=document.getElementById('btn1');
     	var oUl=document.getElementById('ull');
     	var oTxt=document.getElementById('text1');

     	oBtn.onclick=function()
     	{
     		var  oLi=document.createElement('li');//c
     		oLi.innerHTML=oTxt.value;//把otxt的值赋给oUl,然后输出到文本中
     		oUl.appendChild(oLi);
     	};
     };
      
	</script>
</head>
<body>
	<input id="text1" type="text" name="text1">
	<input id="btn1" type="button" value="创建">
	<ul id=ull>
		
	</ul>
</body>
</html>

```
 - 插入元素
  1.insertBefore(节点，原有节点) 在已经有的节点前插入
下面来看代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>插入元素</title>
	
	<script >
     window.onload=function()
     {
     	var oBtn=document.getElementById('btn1');
     	var oUl=document.getElementById('ull');
     	var oTxt=document.getElementById('text1');

     	oBtn.onclick=function()
     	{
     		var  oLi=document.createElement('li');//c
     		var aLi=oUl.getElementsByTagName('li');
     		oLi.innerHTML=oTxt.value;//把otxt的值赋给oUl,然后输出到文本中
     		//oUl.appendChild(oLi);
     		if(aLi.length>0)//判断如果有元素就在它之前插入,否则从第一个开始创建。
     		{
     			oUl.insertBefore(oLi,aLi[0]);
     		}
     		else
     		{
     			oUl.appendChild(oLi);
     		}
     	};
     };
      
	</script>
</head>
<body>
	<input id="text1" type="text" name="text1">
	<input id="btn1" type="button" value="创建">
	<ul id=ull>
		
	</ul>
</body>
</html>

```
- 删除元素节点
1.removeChild(删除元素)
看下面代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
     	var aA=document.getElementsByTagName('a');
     	var oUl=document.getElementById('ull');

     	for(var i=0;i<aA.length;i++)
     	{
     		aA[i].onclick=function()
     		{
     			oUl.removeChild(this.parentNode);
     		};
     	}
     };

	</script>
</head>
<body>
	
	<ul id=ull>
	<li >123<a href="javascript:;">删除</a></li>
	<li>456 <a href="lavaseript:;">删除</a></li>
	</ul>
</body>
</html>

```
#表格应用
- 获取 
1.tBodies、tHead、tFoot、rows、cells
下面来看代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
     	var oTab=document.getElementById('tab1');
     	alert(oTab.tBodies[0].rows[1].cells[1].innerHTML);
     	
     };

	</script>
</head>
<body>
	
	<table id="tab1"border="1" width="600">
		<tbody>
		<head>
           <td>id</td>
           <td>名字</td>
           <td>年龄</td>
		</head>
		<tr>
				<td>1</td>
				<td>one</td>
				<td>12</td>
			</tr>
			<tr>
				<td>2</td>
				<td>two</td>
				<td>16</td>
			</tr>
			<tr>
				<td>3</td>
				<td>three</td>
				<td>20</td>
			</tr>
			<tr>
				<td>4</td>
				<td>four</td>
				<td>25</td>
			</tr>
	   </tbody>
	</table>
</body>
</html>

```
- 隔行变色
下面来看代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
     	var oTab=document.getElementById('tab1');
     	var oldColor='';

     	for(var i=0;i<oTab.tBodies[0].rows.length;i++)
     	{
     		oTab.tBodies[0].rows[i].onmouseover=function()
     		{
     			oldColor=this.style.background;
     			this.style.background='green';
     		};

     		oTab.tBodies[0].rows[i].onmouseout=function()
     		{
     			this.style.background=oldColor;
     		};

     		if(i%2)
     		{
     			oTab.tBodies[0].rows[i].style.background='';
     		}
     		else
     		{
     			oTab.tBodies[0].rows[i].style.background='#ccc';
     		}
     	}

     };

	</script>
</head>
<body>
	
	<table id="tab1"border="1" width="600">
		<tbody>
		<head>
           <td>id</td>
           <td>名字</td>
           <td>年龄</td>
		</head>
		<tr>
				<td>1</td>
				<td>one</td>
				<td>12</td>
			</tr>
			<tr>
				<td>2</td>
				<td>two</td>
				<td>16</td>
			</tr>
			<tr>
				<td>3</td>
				<td>three</td>
				<td>20</td>
			</tr>
			<tr>
				<td>4</td>
				<td>four</td>
				<td>25</td>
			</tr>
	   </tbody>
	</table>
</body>
</html>

```
- 表格添加和删除
1、添加操作。
   直接看代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
     	var oTab=document.getElementById('tab1');
     	var oldColor='';

     	for(var i=0;i<oTab.tBodies[0].rows.length;i++)
     	{
     		oTab.tBodies[0].rows[i].onmouseover=function()
     		{
     			oldColor=this.style.background;
     			this.style.background='green';
     		};

     		oTab.tBodies[0].rows[i].onmouseout=function()
     		{
     			this.style.background=oldColor;
     		};

     		if(i%2)
     		{
     			oTab.tBodies[0].rows[i].style.background='';
     		}
     		else
     		{
     			oTab.tBodies[0].rows[i].style.background='#ccc';
     		}
     	}

     };

	</script>
</head>
<body>
	
	<table id="tab1"border="1" width="600">
		<tbody>
		<head>
           <td>id</td>
           <td>名字</td>
           <td>年龄</td>
		</head>
		<tr>
				<td>1</td>
				<td>one</td>
				<td>12</td>
			</tr>
			<tr>
				<td>2</td>
				<td>two</td>
				<td>16</td>
			</tr>
			<tr>
				<td>3</td>
				<td>three</td>
				<td>20</td>
			</tr>
			<tr>
				<td>4</td>
				<td>four</td>
				<td>25</td>
			</tr>
	   </tbody>
	</table>
</body>
</html>

```
- 删除
代码出现BUG，目前还不知道问题出现的地方
先来看代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
 		var oTab=document.getElementById('tab1');
 		var oBtn=document.getElementById('btn1');
 		var oName=document.getElementById('name');
 		var oAge=document.getElementById('age');
 		var id=oTab.tBodies[0].rows.length+1;

 		oBtn.onclick=function()
 		{
 			var oTr=document.createElement('tr');

 			var oTd=document.createElement('td');
 			oTd.innerHTML=id++;
 			oTr.appendChild(oTd);

 			var oTd=document.createElement('td');
 			oTd.innerHTML=oName.value;
 			oTr.appendChild(oTd);

 			var oTd=document.createElement('td');
 			oTd.innerHTML=oAge.value;
 			oTr.appendChild(oTd);

 			oTab.tBodies[0].appendChild(oTr);

 			var oTd=document.createElement('td');
 			oTd.innerHTML='<a href="javascript:;">删除</a>';
 			oTr.appendChild(oTd);

 			oTd.getElementByTagname('a')[0].onclick=function()
 			{
 				oTab.tBodies[0].removeChild(this.parentNode.parentNode);
 			};
 			oTab.tBodies[0].appendChild(oTr);
 		};

};

	</script>
</head>
<body>
	姓名:<input id="name" type="text" />
	年龄:<input id="age" type="text" />
	<input  ID="btn1" type="button" value="添加"/>
	
	<table ID="tab1"border="1" width="600">
		<tbody>
		<head>
           <td>id</td>
           <td>名字</td>
           <td>年龄</td>
           <td>操作</td>
		</head>
		<tr>
				<td>1</td>
				<td>one</td>
				<td>12</td>
				<td></td>
			</tr>
			<tr>
				<td>2</td>
				<td>two</td>
				<td>16</td>
				<td></td>
			</tr>
			<tr>
				<td>3</td>
				<td>three</td>
				<td>20</td>
				<td></td>
			</tr>
			<tr>
				<td>4</td>
				<td>four</td>
				<td>25</td>
				<td></td>
			</tr>
	   </tbody>
	</table>
</body>
</html>

```

- 排序
下面来看代码
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	
	<script >
     window.onload=function()
     {
 	   var oTab=document.getElementById('tab1');
 	   var oBtn=document.getElementById('btn1');

 	  oBtn.onclick=function()
 	  {
 	  	var arr=[];

 	  	for(var i=0;i<oTab.tBodies[0].rows.length;i++)
 	  	{
 	  		arr[i]=oTab.tBodies[0].rows[i];
 	  	}
 	  	arr.sort(function(tr1,tr2){
          var n1=parseInt(tr1.cells[0].innerHTML);
          var n2=parseInt(tr2.cells[0].innerHTML);

          return n1-n2;
 	  	});
 	  	for (var i=0;i<arr.length;i++)
 	  	{
 	  		oTab.tBodies[0].appendChild(arr[i]);
 	  	}
 	  };
};

	</script>
</head>
<body>
	

	<input  id="btn1" type="button" value="排序"/>
	
	<table ID="tab1"border="1" width="600">
		<tbody>
		<head>
           <td>id</td>
           <td>名字</td>
           <td>年龄</td>
           <td>操作</td>
		</head>
		<tr>
				<td>1</td>
				<td>one</td>
				<td>12</td>
				<td></td>
			</tr>
			<tr>
				<td>4</td>
				<td>two</td>
				<td>16</td>
				<td></td>
			</tr>
			<tr>
				<td>3</td>
				<td>three</td>
				<td>20</td>
				<td></td>
			</tr>
			<tr>
				<td>2</td>
				<td>four</td>
				<td>25</td>
				<td></td>
			</tr>
	   </tbody>
	</table>
</body>
</html>

```
#JS运动基础
- 匀速运动
1.废话不多说直接看例子
```

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>创建子节点</title>
	<style type="text/css">
		#div1{width: 200px;height: 200px;background: yellow;position: absolute;top: 50px;left:0px;}
	</style>
	<script >
     var timer=null;

     function startMove()
     {
     	var oDiv=document.getElementById('div1');

     	clearInterval(timer);//关闭定时器
     	timer=setInterval(function(){
     		var  speed=1;

     		if(oDiv.offsetLeft>=300)//判断如果是到了300就停止，否则就继续直到300为止，这样不会有超出的问题
     		{
     			clearInterval(timer);
     		}
     		else
     		{
     			oDiv.style.left=oDiv.offsetLeft+speed+'px';
     		}
     	},30);
     }

	</script>
</head>
<body>
	

		<input  id ="btn1" type="button" value="开始运动" onclick="startMove()"/>
		<div id="div1">
			
		</div>
</body>
</html>

```
#三、js事件
- 键盘事件
1.   keycode

#四、Ajax基础