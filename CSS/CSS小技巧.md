### 1. 如何使得导航栏漂浮在背景图片上<br>
* 通过以下代码就可实现
```css
.header {
    display: flex;  
    justify-content: center;/* 设置水平居中 */
    align-items: center;/* 设置垂直居中 */
    border-radius: 2px; 
    margin-top: 50px;
    position: absolute;
    z-index: 10;
    width: 100%;
    opacity: 0.8;
}

```
![导航栏飘浮在背景上](https://github.com/wangxinyu123/SKill/blob/master/JavaScript/Img/header.png)<br>

### 2.设置样式的时候千万要小心<br>
* 那就是选择器的权重问题   
```css
/*常用的选择器*/
   
   *{通配符}
   #btn{id选择器}
   .btn{类选择器}
   p 元素选择器
   伪类选择器 --> a:link, a:visited, a:hover, a:active
   子元素选择器 div.page1:nth-of-type(2)

```

* 权重大小<br>
!important > 行内样式 > id选择器 > 类选择器 > 元素/伪类选择器 > *  <br>
  
### 3.三种方法使得元素消失<br>  

* display:none; 很好理解就是把元素从页面删除他所占有的位置有其他元素替代,造成页面的重绘重排<br>   
* visibility: hidden; 根据英文大概翻译就是看不见,但是不会造成重排<br>   
* opacity: 0;  改变透明度达到效果,但是绑定的事件依旧可以触发<br>
> 通过 opacity: 0; 实现的排版<br>
[代码传送门](https://github.com/wangxinyu123/ShoesMall/blob/master/shoespos/src/common/leftNav.vue)

```css
       
.classification dl dd  span{
        opacity: 0;
    }
    
 <div class="classification">
       <dl>
          <dd><router-link to="/login">注册会员</router-link><span>|</span></dd>
          <dd><router-link to="/login">登录</router-link><span>|</span></dd>
       </dl>
 </div>

```
### 4.如何实现三角形<br>
* 让我们看一下变化的过程<br>
<img src="https://github.com/wangxinyu123/SKill/blob/master/CSS/img/CSS%E4%B8%89%E8%A7%92%E5%BD%A2(1).png" width="375">
<img src="https://github.com/wangxinyu123/SKill/blob/master/CSS/img/CSS%E4%B8%89%E8%A7%92%E5%BD%A2(2).png" width="375"><br>
<img src="https://github.com/wangxinyu123/SKill/blob/master/CSS/img/CSS%E4%B8%89%E8%A7%92%E5%BD%A2(3).png" width="375"><br>

```css

    div{
        width: 0px;
        height: 0px;
        margin: 100px auto;
        border-bottom: 80px solid skyblue;
        border-left: 80px solid transparent;
        border-right: 80px solid transparent;      
    }

``` 
### 5.三步解决超出文本内容<br>

```css

overflow: hidden; 内容会被修剪，并且其余内容是不可见的。

white-space：nowrap; 文本会在同一行 知道遇到</br>才会换行

text-overflow: ellipsis; 显示省略符号来代表被修剪的文本。

```
### 6.如何通过flex达到效果<br>

* flex布局比起通过定位布局更加方便

```css
/**
  flex一定要在父级元素写
*/

.father{

     display:flex;  
     justify-content: center; 水平方向
     align-items: center; 垂直方向
  } 
  

```

```css
/**
 用于左列定宽 右侧自适应填满
*/
#Box{
    display:flex;
    width: 100%;
    height: 400px;
  }
.left{
    width:100px;
    height: 400px;
  }
.right{
    flex:1;
    height: 400px;
  }  
  
   <div id="Box">
       <div class="left">left</div>
       <div class="right">right</div>
   </div>
    
```



