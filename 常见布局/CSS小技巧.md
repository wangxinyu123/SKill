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
