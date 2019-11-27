### CSS的两种盒模型<br>
* box-sizing: border-box<br>
整体的内容都包括在高度内<br>

```css
    div{
        box-sizing: border-box;
        height: 100px;
        width: 100px;
        background-color: bisque;
        padding:5px;
        margin: 10px;
      }
``` 
![](https://github.com/wangxinyu123/SKill/blob/master/CSS/img/border-box.png)<br>
* box-sizing: content-box<br>
如果再加上外边距和内边距高度会在内容高度的基础上增加<br>

```css
    div{
        box-sizing: content-box;
        height: 100px;
        width: 100px;
        background-color: bisque;
        padding:5px;
        margin: 10px;
    }

```   

![](https://github.com/wangxinyu123/SKill/blob/master/CSS/img/content-box.png)
