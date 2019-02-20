# travel

> A Vue.js project

## 一 前期初始化


1. 适配适配移动端
```
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0">
```
2. 引入样式初始化文件 以及解决移动端border边框
```
border.css reset.css
 ```
3. 解决移动端点击事件延迟300毫秒
```
1 npm fastclick 2 import fastClick from 'fastclick' 3 fastClick.attach(document.body)
```

## 首页部分

1. 引入字体图标
```
import '../assets/styles/iconfont.css'
```
2. 优化代码
```
 resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
      '@': resolve('src'),
      'styles': resolve('src/assets/styles'), //设置路径
    }
  }

  @import '~styles/varibles.less'; //在style标签中使用简写路径要在import前加@,简写属性前加~
```

## git分支的使用
1. 创建分支: git branch dev
 -  在刚创建时dev分支和master 分支内容一样
2. 切换分支: git checkout dev
3. 合并分支: git merge dev
- 把当前分支与指定分支合并
4. 查看分支: git branch 
5. 设置上游分支 git push --set-upstream origin index-swiper
6. 推送上游分支 git push origin

### git使用流程
1. git add . 缓存当前分支
2. git commit -m 'message' 储存分支
3. git pus 提交到github分支
4. git checkout master 切换到主分支
5. git merge dev 把线上的dev分支合并到主分支 //origin/dev
6. git push 把master的内容提交到github

## 首页轮播图
1. Vue-Awesome-Swiper轮播图插件的使用 
- npm install vue-awesome-swiper@2.6.7 --save //安装
2. 解决轮播图未加载出来时 下面的元素闪到上面
```
.warpper {
  width: 100%;
  height: 0;
  padding-bottom: 37.5%;
  overflow: hidden;
```

##Icons 页面
1. 加载图片还是用padding方式流出位置
```
position: relative;
    width: 25%;
    height: 0;
    padding-bottom: 25%; 
    float: left;

    position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0.4rem; //利用絕對定位留出下面的位置
      box-sizing: border-box;

       position: absolute;
      line-height: 0.4rem;
      bottom: 0;
      left: 0;
      right: 0; //left和right設置為0 讓元素寬度自動100%
      height: 0.4rem; //利用絕對定位留出下面的位置
      text-align: center;
```
2. 图标用数据实现
3. 把图标页面做成可以左右切换
```
+超出八个图标切换到第二页,利用双循环实现
  computed: {
    pages () {
      const pages = []
      this.iconsList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
```
4.  解决文字溢出部分用省略号显示
```
.ellipsis() {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```
5. less导出样式代码段
```
+ 定义:
.ellipsis() {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

+引用
@import '~styles/mixins.less'; 导入
.icon-desc {
      position: absolute;
      line-height: 0.4rem;
      bottom: 0;
      left: 0;
      right: 0;
      height: 0.4rem;
      text-align: center;
      .ellipsis(); //使用
    }
```

## recommend 推荐部分
1. button不要设置高度,用padding自动挤出
```
 .item-button {
      // width: .75rem;
      // height: .2rem;
      background-color: #ff9300;
      border-radius: 0.03rem;
      margin-top: 0.1rem;
      line-height: 0.2rem;
      font-size: 0.12rem;
      padding: 0 0.1rem;
    }
```
2. .ellipsis();多出文本不能等显示省略号解决方法
```
+在父元素加上min-width:0

  .item-info {
    flex: 1;
    padding: 0.05rem;
    min-width: 0;
    .item-title {
      line-height: 0.25rem;
      font-weight: bold;
      .ellipsis();
    }
    .item-desc {
      line-height: 0.2rem;
      color: #cccccc;
      .ellipsis();
    }
```
## 周末去哪儿部分
1. 直接复制recommend部分
2. 注意有图片部分都用padding挤出方式

## 通过axios获取首页数据
1. 安装axios
2. 在.gitignore文件中配置禁止git上上传数据文件到github
```
.DS_Store
node_modules/
/dist/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
static/mock  //禁止同步到github
```
3. 在congig文件下配置访问地址
```
 proxyTable: {
      '/api': {
        target: 'http://localhost:8080', 把请求转发到8080当前服务器端口
        pathRewrite: {
          '^/api': '/static/mock'  //当ajax访问api的时候 把api替换成/static/mock
        }
      }
    },
```
4. 在生命周期函数mounted里面请求ajax请求
```
 methods: {
    getHomeinfo () {
      axios.get('/static/mock/index.json')
        .then(this.getHomeinfoSucc)
    },
    getHomeinfoSucc (res) {
      console.log(res)
    }
  },
  mounted () {
    this.getHomeinfo()
  }
```
5. 把数据从父组件传递给子组件
```
 getHomeinfoSucc (res) {
      res = res.data
      console.log(res)
      if (res.ret && res.data) {
        const data = res.data
        this.city = data.city
      }
    }
```

6. 解决渲染轮播图时当前图片为最后一张
```
<swiper
      :options="swiperOption"
      v-if="showSwiper"  //通过vif判断来渲染轮播图
    >

computed: {  //在computed计算属性里判断list数据是否接受到了然后渲染
    showSwiper () {
      return this.list.length
    }
  }
```
7. city路由页面创建
8. search页面
## 城市列表部分
1. 按钮不要设置宽高,通过padding
2. 滚动屏幕 better-scroll使用
```
<div class="list" ref="wrapper"></div>  //ref获取DOM元素

import Bscroll from 'better-scroll'
export default {
  name: 'cityList',
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  }
}
```
## 创建屏幕右侧字母表alphabet 组件
```
.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  right: 0;
  top:.86rem;
  bottom:0rem;
  width: .2rem;
  .item {
    width: 0.2rem;
    color: @bgColor;
    text-align: center;
    line-height: .2rem;
  }
}
```

##城市列表页面数据渲染
1. 循环对象
```
 <div
        class="area"
        v-for="(item, key) in cities"   //item为对象的键 key为对象的值
        :key="key"         
      >
```
2. 循环数组
```
 <div
            class="button-warpper"
            v-for="item in hotCities"   //循环数组不用加index
            :key="item.id"
          >
```



