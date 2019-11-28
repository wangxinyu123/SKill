### Position 几个属性的作用<br>

> 今天说一说 relative, absolute, fixed，static <br>

* static: 默认位置. 遇到继承的情况，我们不愿意见到元素所继承的属性影响本身<br>
从而可以用Position:static取消继承，即还原元素定位的默认值   
* relative: 相对定位 相对于元素默认为进行定位 通过设置top, bottom, left, right<br> 
* absolute: 绝对定位 相对与父元素, 当元素设置为绝对定位后会造成脱离文档流<br>
* fixed: 固定定位 可定位到指定坐标, 且不会跟随窗口滚动设置后也会脱离文档流<br>

```css
/*
  父级元素相对定位, 子集元素绝对定位
  这样可以达到覆盖的效果
  例如: '优惠券' '轮播图'
*/

  .Box1{  
     width: 30px;
     height: 30px;
     position: relative;
  }
  .Box2{
     width: 30px;
     height: 30px;
     position: absolute;
     content:'';
  }

    <div class="Box1">
        <div class="Box2"></div>
    </div>

```
