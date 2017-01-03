#### **JavaScript奇技淫巧**  
***

##### 正数向下取整

`var a = ~~1.2;  //1`   
或  
`var a = 3.4>>0; //3 `

##### 使用+号转换时间戳或数字  

```javaScript
var time = + new Date();
var a = '-123';
console.log(+a); // -123
```

##### 数组传递和复制

```javaScript
var a = [1,2,3];  
var b = a;    
delete b[i];
console.log(a);//[1, undefined × 1, 3]

var a = [4,5,6];
var b = a.slice(0);
delete b[1];
console.log(a);//[4,5,6]
console.log(b);//[4, undefined × 1,6]
```
##### 字符串拼接

```javaScript
2.toString();//SyntaxError
2 .toString(); //"2"
2..toString(); //"2"
(2).toString(); //"2"

[1,[2,"abc","",0,null,undefined,false,NaN],3].toString();

```

##### for in 暴露原型链属性

```javaScript
Object.prototype.foo = 1;

var obj = new Object();
obj.bar = 1;
for(var p in obj){
    console.log(p);//bar,foo 都遍历出来了。可以用hasOwnProperty()过滤原型链属性

}
```
##### 不使用第三变量交换值

`a= [b, b=a][0];`

##### 将一个数组插入另一个数组的指定位置

```javaScript
var a = [1,2,3,7,8,9];
var b = [4,5,6];
var insertIndex = 3;
a.splice.apply(a, Array.concat(insertIndex, 0, b));
// a: 1,2,3,4,5,6,7,8,9

```

##### 快速取数组最大和最小值

```javaScript
Math.max.apply(Math, [1,2,3]); //3
Math.min.apply(Math, [1,2,3]); //1
```
##### 条件判断

```javaScript
var a = b && 1;
//相当于:
if (b) {
  a = 1;
}else {
  a = b;
}

var a = b || 1;
//相当于
if (b) {
  a = b;
} else {
  a = 1;
}
```

##### 判断浏览器是否为IE

`var ie = /*@cc_on !@*/false;`

##### 将变量转换成Boolean类型

```
var a = 1;
console.log(!!a) //true
```
##### Timeout中获取其作用域外的变量
```javaScript
//以下这段无法取到正确的i结果
for(var i = 0; i < 10; i++) {
    setTimeout(function(){
        console.log(i);
    },100);
}

//修改后的代码
for(var i = 0; i < 10; i++) {
    (function(i){
        setTimeout(function(){
            console.log(i);
        },100)
    })(i);
}

```

##### 位移符的应用

```javaScript
var num = 10 >> 1; // 相当于10 / 2，但是效率更高 
console.log(num) // 5;

var num = 2 << 3; // 2的四次方
console.log(num) // 16;
```

##### 通过字符串调用方法

```javaSript
function sayHello(str) {
   return 'hello ' + str;
}

var functionName = "say"+"He"+"llo";
var fn = window[functionName];
console.log(fn('world')); // hello world

```

##### 去除数组中重复的值

```javaScript
function removeRepeat(arr){
  return arr.filter(function(elem, pos) {
    return arr.indexOf(elem) == pos;
  });
}
var arr = new Array("1","2","3","4","4","4","4","5");
var newArr = removeRepeat(arr);
console.log(newArr); //1,2,3,4,5

```
