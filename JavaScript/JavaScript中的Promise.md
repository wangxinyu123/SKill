**前言**

>  **此篇文章过于基础,大佬可以忽略但是欢迎评论提出错误和补充,谢谢💩**   
> 大家都知道js是单线程,单线程就意味着，所有任务需要排队，前一个任务结  束，才会执行后一个任务。如果前一个任务耗时很长，后一个任务就不得不一直等着。
***   
   
> 任务队列分为两种 一种是同步任务（synchronous），另一种是异步任务（asynchronous）。同步任务指的是，在主线程上排队执行的任务，只有前一个任务执行完毕，才能执行后一个任务；异步任务指的是，不进入主线程、而进入"任务队列"（task queue）的任务，只有"任务队列"通知主线程，某个异步任务可以执行了，该任务才会进入主线程执行。

![](https://user-gold-cdn.xitu.io/2019/11/10/16e54510179a3097)
**[图片参考](https://juejin.im/post/5b498d245188251b193d4059#heading-8)**
   
> js异步有一个机制，就是遇到宏任务，先执行宏任务，将宏任务放入eventqueue，然后在执行微任务，将微任务放入eventqueue最骚的是，这两个queue不是一个queue。当你往外拿的时候先从微任务里拿这个回掉函数，然后再从宏任务的queue上拿宏任务的回掉函数。 我当时看到这我就服了还有这种骚操作。
      
 **1.1**    
 通过下面的练习大家应该会进一步的理解
 >简单的入门例子
 
 ```js
 console.log(1);
 setTimeout(function(){console.log(2);},0);//1, 2立即执行
 ```
 
 >这是因为setTimeout是宏任务   
 >要进入队列等到输出'3'之后才会打印2  
 
 ```js
 setTimeout(function(){console.log(2);},0);
 console.log(3);//3 ，2
 ```
 

![](https://user-gold-cdn.xitu.io/2019/11/10/16e5451edbc6f5d8?w=938&h=434&f=png&s=55223)
 
 > 接下来的例子非常有意思 😉   
 


![](https://user-gold-cdn.xitu.io/2019/11/10/16e54522d64143d1?w=922&h=1174&f=png&s=226770)
 
 > 一脸懵逼的结果 😳 
 

![](https://user-gold-cdn.xitu.io/2019/11/10/16e545249e601d51?w=872&h=794&f=png&s=104464)
 
 **下面是我的理解(仅供参考)**   
  
> 1 ) 程序都是从上向下执行 所以输出global毫无疑问   
 2 ) 遇到第一个setTimeout => 宏任务 进入队列   
 3 ) for循环输出里面是setTimeout进入队列 然后输出 1,2,3,4,5   
 4 ) 遇到了构造函数Promise 输出promise1 接着走我们遇到了then => 微任务 push进入队列   
 5 ) 第二个setTimeout => 宏任务 进入队列   
 6 ) 依旧是构造函数 输出promise2 这里还有一个then push队列   
 7 ) 到这里我们总结一下 目前队列里面有setTimeout(宏任务) Promise.then(微任务) 这两类 优先输出微任务  
 8 ） 走了一遍之后宏任务都在队列,此时输出微任务的 then1 和 then2   
 9 ) 因为是异步执行的在 步骤3循环之后的第6s 定时器的6也已经好了对于为什么不是5的同学可以去看一下ES6的语法   
 10 ）所以现在接着for循环执行 到了第二个setTimeout 输出 'timeout2' 和 'timeout2-promise' 又遇到了then push队列并且立即执行输出 'timeout2-then'    
 11 ）同理可得 延迟两秒依次输出 timeout1  timeout1-promise timeout1-then 这里的三个内容几乎是同时输出   
 12 ）现在到了for循环里的setTimeout 每隔一秒输出一个6
   
**1.2 小试牛刀**   
> stackoverflow 上的题目   
   
```js

resolve(resolvedPromise)
//等价：
Promise.resolve().then(() => resolvedPromise.then(resolve));


```
 
```js
let resolvePromise = new Promise(resolve => {
  let resolvedPromise = Promise.resolve()
  resolve(resolvedPromise)//放到队列的后面执行
})
resolvePromise.then(() => {
  console.log('resolvePromise resolved')
})
let resolvedPromiseThen = Promise.resolve().then(res => {
  console.log('promise1')
})
resolvedPromiseThen
  .then(() => {
    console.log('promise2')
  })
  .then(() => {
    console.log('promise3')
  })

```
> 输出结果:   
> 
> promise1 => promise2 =>   resolvePromise resolved => promise3

 **1.3 感受总结** (有错误欢迎大佬提issue)

   >遇到宏/微观任务进队列 每执行完一遍程序的过程, 结束后要保证队列是空的 说一千道一万 主要是取决于then()这个微任务   
      
*  遇到 async 立即执行 遇到 await 调转到后面对应的函数   
    
*  resolve()里面具体内容要放到队列里面继续执行后面的代码</br>
  
*  没走依次循环可以画图看一下宏任务,微任务是否还存在,如果存在  
   按照顺序先执行微任务 后执行宏任务   

**参考**
 
 [彻底理解setTimeout](https://www.jianshu.com/p/3e482748369d?from=groupmessage)   
[任务，微任务，队列和时间表](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/?utm_source=html5weekly)