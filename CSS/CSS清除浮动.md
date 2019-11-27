## CSS浮动篇<br>
* 浮动后的元素脱离文档流,会造成页面整体布局的错乱
* 要么大家一起浮动要么清除浮动,常用的两种清除浮动的方法

```css
/*
 浮动会造成高度塌陷,
 这就是我们要清除浮动的理由
*/

        #container {
            border: 5px solid orange;
        }

        .div1 {
            width: 100px;
            height: 100px;
            margin-right: 20px;
            background-color: antiquewhite;
            float: left;
        }
        
        ...
        
    <div id="container">
        <div class="div1">1</div>
        <div class="div2">2</div>
        <div class="div3">3</div>
    </div>     
        
```
![]()<br>

## 如何清除浮动<br>
* clear:both; 可以在后面建立一个空元素进行清除,<br>
或者是在最后一个内容不为空的元素 clear:both;

```css
  
  .div4 {
      clear: both;
      }
      
     <div class="div4"></div>

```
* BFC 形成块级元素 触发条件:<br>


浮动元素（元素的 float 不是 none）

绝对定位元素（元素的 position 为 absolute 或 fixed）

行内块元素（元素的 display 为 inline-block）

overflow 值不为 visible 的块元素

```css

/*
 在父级元素添加  overflow: hidden; 
*/

  #container {
         border: 5px solid orange;
         overflow: hidden; 
       }
       

```
![]()<br>
