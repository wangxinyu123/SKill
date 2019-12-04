### Vue实现吸顶效果<br>

> 通过查找资料实现了吸顶效果,在此总结归纳 如果对你有所帮助可以Star<br>

* 完成的效果<br>
<img src="https://github.com/wangxinyu123/SKill/blob/master/Vue/Img/%E5%AF%BC%E8%88%AA%E6%A0%8F.png" width="100"><br>
<img src="https://github.com/wangxinyu123/SKill/blob/master/Vue/Img/%E5%AF%BC%E8%88%AA%E6%A0%8F%E5%AE%8C%E6%88%90%E5%90%B8%E9%A1%B6.png" width="100"><br>


```html
 <div class="navBar" :class="headerFixed?'isFixed':'' ">

```
```css

.navBar {
  position: relative;
  width: 100%;
  height: 80px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f7f7f7;
}
.isFixed {
  position: fixed;
  top: 0;
  z-index: 999;
}


```

```js

data() {
    return {
       headerFixed: ''
    };

```

```js

  methods: {
    handleScroll() {
      // 得到页面滚动的距离
      let scrollTop =
        window.pageYOffset ||
        document.documentElement.scrollTop ||
        document.body.scrollTop;
        //  当滚动超过 180 时，实现吸顶效果
      if (scrollTop > 180) {
        this.headerFixed = true;
      } else {
        this.headerFixed = false;
      }
    }
  },
  

```

```js

  mounted() {
    // handleScroll为页面滚动的监听回调
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    //同时在destroyed回调中移除监听：
    window.removeEventListener("scroll", this.handleScroll);
  }


```
