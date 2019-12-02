## 手把手教你封装组件<br>

#### 目录如下
![]()<br>

* 先在 components 文件夹下创建js文件
* 再创建 .vue文件里面写入你想要的内容
* 继续在main.js文件里面引用 这样就封装好了
* 代码如下 ⤵️


```js
/*
 wh.js
*/

import WxHeader from './WxHeader';

function plugins(Vue){
    Vue.component('wx-header',WxHeader);

}

export default plugins;


```
```html

/*
 WxHeader.vue
*/

<template>
  <div id="header">
    <div class="header">
      <div class="h-box">
        <div class="nav-logo">
          <h1>
            <a href="#" style="text-decoration:none; color:white;">ShoesMall</a>
          </h1>
        </div>
        <div class="right-box">
          <div class="nav-list">
            <el-input
              placeholder="请输入商品信息"
              suffix-icon="el-icon-search"
              v-model="input1"
              class="nav-input"
            ></el-input>
            <a
              style="color:white; width:120px; text-decoration:none; margin-left:20px;"
              href="#"
            >全部商品</a>
            <router-link to="/login">
              <a
                class="el-icon-user-solid"
                style="font-size:28px; color:white; margin-left: 20px; text-decoration:none;"
              ></a>
            </router-link>
            <span style="font-size:28px; margin-left: 20px;">|</span>
            <a class="icon iconfont icon-gouwuchekong" style="font-size:28px; margin-left: 20px;"></a>
          </div>
        </div>
      </div>
    </div>
    <div class="navbar">
      <div class="nav-content">
        <ul>
          <li>
            <router-link to="/">首页</router-link>
          </li>
          <li>
            <a href="#">全部</a>
          </li>
          <li>
            <a href="#">品牌周边</a>
          </li>
          <li>
            <a href="#">促销活动</a>
          </li>
          <li>
            <a href="https://github.com/wangxinyu123">Github</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<style>
.header {
  height: 100px;
  width: 100%;
  background-color: black;
}
.h-box {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  margin-left: 150px;
  margin-right: 150px;
}
.right-box {
  display: flex;
}
.h-box .nav-list {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 22px;
}
.nav-list input {
  width: 200px;
  height: 40px;
  border-radius: 4px;
}
.el-input__icon {
  width: 85px;
}
.el-input__inner:hover {
  box-shadow: 2px 2px 5px rgb(92, 96, 97) inset;
  transition: 0.5s all linear;
}
.el-icon-user-solid {
  margin-left: 5px;
}
.navbar {
  width: 100%;
  height: 80px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
  display: flex;
  justify-content: center;
  align-items: center;
}
.nav-content {
  width: 100%;
  height: 50%;
  margin-left: 340px;
  margin-right: 340px;
}
.nav-content ul li {
  list-style: none;
  float: left;
  margin-right: 40px;
}
.nav-content ul li a {
  text-decoration: none;
  color: black;
}
</style>
<script>
export default {
    name:'wx-header',
  data() {
    return {
      input1: ""
    };
  }
};
</script>


```


```js
/*
 main.js
*/

import plugins from './components/common/wh'
Vue.use(plugins);


```