### Js数据类型<br>   

* 基本数据(值)类型: String, Number, Boolean, Null, undefined
* 对象(引用)类型: Object, Function, Arrary   
* 判断<br>


```css
1.typeof  返回数据类型的字符串表达式  
2.instance of  判断对象的具体类型返回布尔值
3.=== 可以判断 null, undefined

```
```js

/*
 typeof 可判断String, Number, Boolean, undefined, function
 不能判断 null与object  object与Array
*/

var a ;
console.log(a)
console.log(typeof a);
console.log(typeof a==='undefined');
console.log(a===undefined);//undefined 'undefined' true true

console.log(undefined==='undefined');//false

a = 4;
console.log(typeof a==='number');//true

a = 'wxy';
console.log(typeof a === 'string');//true

a=true;
console.log(typeof a === 'boolean');

a=null;
console.log(typeof a);//object

```
```js

var a1 = {
  a2:[1,'abc',console.log],
  a3:function(){
  console.log('a3');
return function(){
  return 'wxy';
   }
 }

}
console.log(a1 instanceof Object);// true
console.log(a1.a2 instanceof Object, a1.a2 instanceof Array);//true true
console.log(a1.a3 instanceof Function, a1.a3 instanceof Object);// true true
console.log(a1.a3()()); //a3 wxy

```
### 思考undefined与null的区别?
* undefined代表定义未赋值
* null定义并赋值了,只是值为null 