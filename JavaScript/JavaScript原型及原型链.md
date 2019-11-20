### 构造函数<br>
```js
function parent(name,age){
   this.name = name;
   this.age = age;
}

var me = new parent('wxy',21);
console.log(me.name); 
console.log(me.age); // wxy 21

```   
> 实例成员: 通过this添加;   
实例成员只能通过实例化对象访问   
    

### 原型<br>   
```js
function parent(name,age){
   this.name = name;
   this.age = age;
}
parent.prototype.money = function(){
   console.log('今天收入100元');
}
function child(name,age){
   parent.call(this,age,name);
   this.score = score;
}
child.prototype.exam = function(){
   console.log('今天考了98分');
}
child.prototype = new parent();
var child1 = new child();
```
`注意的点`   
> 采用原型链继承会改变parent的内容 而构造函数继承则无法获取父级的原型属性   
> 所以我们采用 构造函数继承和原型链继承相结合的方法实现 这种写法相当于新开辟一个空间,起到中转站的作用
> 公共的方法放到原型对象的身上,节省内存   
> 还不明白的小伙伴 请看下面的图   


![](https://github.com/wangxinyu123/SKill/blob/master/JavaScript/Img/%E5%8E%9F%E5%9E%8B.png)   
<br>
### 原型链<br>
<br>    
> 个人理解: 每个对象都有一个_proto_指向构造函数的prototype原型对象,而原型对象也有_proto_指向上一个构造函数的prototype以此类推一直向上查找知道Object为止(null)
   
=
<br> 
`图片可说明一切`  

![](https://github.com/wangxinyu123/SKill/blob/master/JavaScript/Img/%E5%8E%9F%E5%9E%8B%E9%93%BE.png)
<br>

```

parent.prototypr.sex = '男';
child.sex = '女';

结果输出: 女 (就近原则)
```   
  
