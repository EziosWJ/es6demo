# Es6

## 一、let 和 const声明变量

**var**

* 可以重复声明
* 没有块级作用域
* 无法限制修改

-------------------

### **let** 不能重复声明 变量-可以修改

> ​        let a = 5
>
> ​        // let a = 1; 'a' has already been declared
>
> ​        alert(a)

### **const** 不能重复声明 常量-不可修改

> ​        const a = 5
>
> ​        // a = 76 //Uncaught TypeError: Assignment to 	  constant variable.
>
> ​        alert(a)

### **块级作用域**

>
>
>​       {
>
>​            let a = 5
>
>​            console.log(a)
>
>​        }
>
>​        console.log(a)
>
>​    	//Uncaught ReferenceError: a is not defined

### **块级作用域代表性作用**

* 错误写法

> ​        window.onload=function(){
>
> ​        var aBtn = document.getElementsByTagName('input')
>
> ​	for (var i = 0; i < aBtn.length; i++) {
>
> ​            	aBtn[i].onclick = function(){
>
> ​                console.log(i);
>
> ​           	 }
>
> ​	}

结果都是 `3`

* 改造循环

> ​        for (var i = 0; i < aBtn.length; i++) {
>
> ​            (function(i){
>
> ​                aBtn[i].onclick = function(){
>
> ​                    console.log(i);
>
> ​                }
>
> ​            })(i)
>
> ​            // !function(i){
>
> ​            //     aBtn[i].onclick = function(){
>
> ​            //         console.log(i);
>
> ​            //     }
>
> ​            // }(i)
>
> ​            
>
> ​        }

* 使用let

> ​        for (let i = 0; i < aBtn.length; i++) {
>
> ​            aBtn[i].onclick=()=>{
>
> ​                console.log(i);
>
> ​            }
>
> ​            
>
> ​        }

补充有关匿名函数：[js中(function(){})()写法](https://blog.csdn.net/h330531987/article/details/66275224)



## 二、函数-箭头函数

### **准备**

1.如果只有一个参数，`（）`可以省略

2.如果只有一个return，`{}`可以省略

### **箭头函数**

>
>
>​        // let show = function(){
>
>​        //     console.log('abc')
>
>​        // }
>
>​        let show = () => console.log('abc')
>
>​        
>
>​        show()
>
>​        const arr = [5,4,66,1]
>
>​        // arr.sort(function(a,b){
>
>​        //     return a-b
>
>​        // })
>
>​        arr.sort((a,b)=>a-b)
>
>​        console.log(arr)

## 三、函数-参数

1. 参数扩展/展开

2. 默认参数

### 参数扩展

1. 收集剩余的参数

> function params(a,b,args...){} 

2. 展开一个数组

>
>
>​        let arr1 = new Array()
>
>​        arr1 = [1,2,3,4,5,6]
>
>​        function params(a,b,c,...args){
>
>​            console.log(a);
>
>​            console.log(b);
>
>​            console.log(c);
>
>​            console.log(args);
>
>​        }
>
>​        params(...arr1)

3. 默认参数

> function(a,b=5,c=3){}

## 四、解构赋值

1. 左右两边结构必须一样
2. 右边必须是个东西
3. 声明和赋值不能分开（必须在一句话里完成）

* 实现

> ​        let [a,b,c] = [1,2,3]
>
> ​        console.log(a,b,c);
>
> ​        
>
> ​        let {q,w,e} = {q:"ni",w:"好",e:"ma？"}
>
> ​        console.log(q,w,e);
>
> ​        
>
> ​        let [json,arr,num,str] = [{json1:"杰森",json2:"杰森2"},[1,2,3],0,"aa"]
>
> ​        console.log(json,arr,num,str);
>
> ​        

* 注意

1. 左右两边结构必须一样
2. 右边必须是个东西
3. 声明和赋值不能分开（必须在一句话里完成）

## 五、数组

### map（映射）

>
>
>​        let arr = [12,5,8]
>
>​        let result = arr.map(item=>{
>
>​            console.log(item);
>
>​            return ++ item 
>
>​        })
>
>​        console.log(result);
>
>​        
>
>​        let score = arr.map(item=>item>5?"通过":"不通过")
>
>​        console.log(score);

### reduce(汇总)

```javascript
        //求和
        let _num = [33,55,9]
        let result = _num.reduce((previous,current,index)=>{
            return previous + current
        })
        console.log(result);

        //求平均
        let result2 = _num.reduce((previous,current,index)=>{
            if( index + 1 === _num.length){ 
                return (previous + current)/_num.length
            }else{
                return previous + current
            }
        })
        console.log(result2);
```

