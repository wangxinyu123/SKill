## 你真的了解this吗?   

* 在看过很多大佬写过的文章和代码后,就像是英语的 ‘就近原则’ 一样,指向最后调用你的那个   
* 一般来说是this指向window   
* 那么通过下面的代码希望会帮助到你   
   
```js
/***
  调用的函数付给声明的对象不需要加"()"
***/
var name = 'window';
 var fun = {
 
  fn:function(){
    console.log(this.name);
  }
}
 var fs = fun.fn;
fs(); //window


```    
   
> 为什么会打印windown呢? 请看 => window.fs();    

```js
/***
注意: 
 在函数中要以逗号结尾
***/
var name = 'window';
 var fun = {
    name : 'local',
  fn:function(){
    console.log(this.name);
  }
}
fun.fn(); // local

```    
   
> 通过上面的两段代码是不是对this的指向有种云开雾散那的感觉    

 
<br>  
## 使用call,apply,bind   
 
* call 是将参数列表作为传递的      
* apply 是将参数放进数组进行传递的
* bind 函数名.bind.(this的使用对象,参数1,,参数2,...)() 

```js

var x ={a:1, b:3};
function add(c,d){
  return this.a + this.b + c + d;
}

add.call(x,3,4); // 11

```
```js

var x ={a:1, b:3};
function add(c,d){
  return this.a + this.b + c + d;
}

add.apply(x,[3,4]); // 11

```
```js

var x ={a:1, b:3};
function add(c,d){
  return this.a + this.b + c + d;
}

add.bind(x,3,4)(); // 11

```
<br>  