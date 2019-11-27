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
!important > 行内样式 > id选择器 > 类选择器 > 元素/伪类选择器 > * 

