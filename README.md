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
## 实现城市列表点击字母联动的效果
1. 给每个循环向定义一个方法
```
  handleLetterClick(e){   //e为电视事件对象
      console.log(e.target.innerText);
    }
```
2. 兄弟组件之间传值 子组件-父组件-子组件
3. 得到字母利用better-scroll实现跳转 在Watch里面监听
```
 <div
        class="area"
        v-for="(item, key) in cities"
        :key="key"
        :ref="key"   //同过key绑定这个dom元素
      >

  watch: {
    cityAlphabet () {
      // console.log(this.cityAlphabet)
      if (this.cityAlphabet) {
        const letter = this.$refs[this.cityAlphabet][0]
        this.scroll.scrollToElement(letter)
      }
    }
  }
```
## 滑动右侧字母左侧列表跟着滑动
1. 把对象cities转换成数组  在computed里面计算属性
```
  computed: {
    letters () {
      const letters = []
      for (const key in this.cities) {
        letters.push(key)
      }
      return letters
    }
  }
```
2. 设置touch函数
```
    handeltouchstart () {
      this.touchstatus = true
    },
    handeltouchmove (e) {
      if (this.touchstatus) {   //判断是否开始滑动
        const startY = this.$refs['A'][0].offsetTop  //求出右侧字母列表到顶部的距离
        const touchY = e.touches[0].clientY - 86    //求出手指到顶部的距离
        const index = Math.floor((touchY - startY) / 20)  //求出索引值
        if (index >= 0 && index < this.letters.length) {
          this.$emit('change', this.letters[index])  //根据索引值传出当前元素
        }
      }
    },
    handeltouchend () {
      this.touchstatus = false
    }
```
## 性能优化
1. 值不变的参数不要放在函数里多次计算
```
updated () {
    this.startY = this.$refs['A'][0].offsetTop   //把值一直不变的参数不要放在函数里多次计算,放在updated里只计算一次  data里面不能计算值
  },
```
2. 函数截流 定义延迟函数
```
    handeltouchmove (e) {
      if (this.touchstatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 86
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
```

## 完成城市搜索功能
1.  v-model="keyword" 绑定关键字
2.  传入cities数据
```
  props: {
    cities: Object
  },
```
3. 在watch里面根据关键字获取数据
```
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {  //设置定时器进行函数截流
        const result = []
        if (!this.keyword) {
          this.list = []
          return this.list
        }
        for (let i in this.cities) {
          this.cities[i].forEach(item => {
            if (item.spell.indexOf(this.keyword) > -1 || item.name.indexOf (this.keyword) > -1) {
              result.push(item)
            }
          })
        }
        this.list = result
      }, 100)
    }
```
4. 在mounted生命周期钩子函数里启动滑动搜索出来的列表
```
 mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  }
```
5. 通过vshow判断如果没有所搜到城市显示
```
      <li
        class="search-item border-bottom"
        v-show="hasNoData"
      >没有匹配的城市</li>

        computed: {   //在computes里面计算 条件语句最好不要卸载html里面
    hasNoData () {
      let flag = this.list.length <= 0
      return flag
    }
  },
```

## vuex的使用
1. 引用stroe 在src文件夹下新建store文件夹
```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  state: {
    city: '北京'
  }
})
```
2. 在main.js里导入vuex文件 并挂载到App实例上
import store from './store/index'

new Vue({
  el: '#app',
  router,
  store,   
3. 把原来通过ajax获取到的city的数据删除替换,不再通过ajax获取
     原来的city替换为 {{this.$store.state.city}}
4. 实现点击热门城市改变vuex里面的city数据
```
@click="handleCityClick(item.name)"  //给热门城市绑定点击事件

  methods: {
    handleCityClick (city) {
      this.$store.dispatch('changeCity',city)   //通过dispatch把changCity派送changeCity方法给ACtions,并传入city值
    }
  },

  export default new Vuex.Store({
  state: {
    city: '上海'
  },
  actions: {
    changeCity (ctx, city) {          //actions调用dispath传过来的changcity方法 ctx表示上下文
      ctx.commit('changeCity', city)  //actions调用commit派送changecity方法给mutations
    }
  },
  mutations: {
    changeCity (state, city) {   //mutations调用actions派送过来的changecity方法改变state里面的city值
      state.city = city
    }
  }
})

``` 
5. 如果改变state没有异步操作或者没有复杂批量操作,组件可以不用调用actions做转发,直接调用mutations  
```
  methods: {
    handleCityClick (city) {
      this.$store.commit('changeCity', city)   //组件直接调用commit
    }


    export default new Vuex.Store({   //不调用actions
  state: {
    city: '上海'
  },
  mutations: {
    changeCity (state, city) {
      state.city = city
    }
  }
})
```
6. 实现搜索和点击列表城市改变当前城市的数据改变
```
 <div
            class="item border-bottom"
            v-for="innerItem in item"
            :key="innerItem.id"
            @click="handleCityClick(innerItem.name)"  //城市列表
          > {{innerItem.name}} </div>
```
```
<li
          class="search-item border-bottom"
          v-for="item in list"
          :key="item.id"
          @click="handleCityClick(item.name)"
        > {{item.name}} </li>
```
##点击选择的城市跳转到首页  路由的编程导航
```
this.$router.push('/')
```
##利用localstorage本地存储当前city
1. 使用trycatch防止浏览器不支持localstorage报错
```
let defaultCity = '上海'
try {
  if (localStorage.city) {
    defaultCity = localStorage.city
  }
} catch (error) {
}

export default new Vuex.Store({
  state: {
    city: defaultCity
  },
  mutations: {
    changeCity (state, city) {
      state.city = city
      try {
        localStorage.city = city
      } catch (error) {}
    }
  }
})

```
## 为了便于后期维护代码 把vuex的store进行拆分
1. index文件
```
import Vue from 'vue'
import Vuex from 'vuex'
import state from './state'
import mutations from './mutations'
Vue.use(Vuex)

export default new Vuex.Store({
  state,
  mutations
})
```
2. mutations文件
```
export default {
  changeCity (state, city) {
    state.city = city
    try {
      localStorage.city = city
    } catch (error) {}
  }
}
```
3. state文件
```
let defaultCity = '上海'
try {
  if (localStorage.city) {
    defaultCity = localStorage.city
  }
} catch (error) {
}

export default {
  city: defaultCity
}

```

## 解决首页城市名显示不完整
```
  .header-right {
    float: right;
    padding: 0 .02rem;
    min-width: .52rem;  //把width改为min-width让字体边宽的时候会自动变宽
    float: right;
    text-align: center;
    color: #fff;
    span {
```
##优化vuex
```
<script>
import {mapState} from 'vuex'
export default {
  name:'HomeHeader',
  computed: {
    ...mapState(['city'])   //...为展开运算符 把vuex里面的state里的city属性映射到当前实例的city属性里  可以传入数组
  }
}
</script>

+import { mapState, mapMutations } from 'vuex'
  methods: {
    handleCityClick (city) {
      // this.$store.commit('changeCity', city)
      this.changeCity(city)                    
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])   //把mutations里的changeCity方法直接映射到当前组件
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
```

##使用keepalive解决每次点击页面都会发送ajax请求  
1. 在程序入口组件app.vue加速keepalive  keepalive使用的时缓存里面的数据
```
  <div id="app">
    <keep-alive>
      <router-view />
    </keep-alive>
  </div>
```
2. home首页发送ajax请求的时候应该把当前城市的名字发送过去
```
import {mapState} from 'vuex'  //引入vuex里的stata
  computed:{
    ...mapState(['city'])   //引入state里面的city属性
  },

methods: {
    getHomeinfo () {
      axios.get('api/index.json?city=' + this.city)  //发送ajax请求的时候把city属性一起发送
        .then(this.getHomeinfoSucc)
    },
```
3. 解决keepalive一直使用缓存当city改变的时候不重新发送ajax请求 
4. keepalive新增activated生命周期函数
```
  data () {
    return {
      lastCity: '',    //data里定义一个lastcity属性
  mounted () {
    this.getHomeinfo()
    this.lastCity = this.city  //当页面加载发送ajax请求的时候放lastcity等于当前state传过来的city
  },
  activated () {
    if (this.city !== this.lastCity) {   //若果state发过来的city不等于上一次的lastcity 重新发送ajax请求 并改变lastcity
      this.lastCity = this.city
      this.getHomeinfo()
    }
  }        
```
##详情部分
1. 创建路由
```
  {
    path: '/detail/:id', //把当前ID传入
    name: 'detail',
    component: Detail
  }
```
##详情banner部分
##详情banner部分画廊
1. 创建一个公共组件
2. 使用swiper
3. propos可以设置默认数据
```
  props: {
    imgs: {
      type: Array,
      default () {
        return ['http://img1.qunarzz.com/sight/p0/1709/e4/e4b97c2fbb4e696a3.img.png_r_800x800_ae927025.png', 'http://img1.qunarzz.com/sight/p0/1709/39/39b5b5a87f82aac2a3.img.jpg_r_800x800_5556a76a.jpg']
      }
    }
  },
```
4. 组件里面不要带入数据,而是父组件传递
```
  data () {
    return {
      imgs: ['http://img1.qunarzz.com/sight/p0/1709/e4/e4b97c2fbb4e696a3.img.png_r_800x800_ae927025.png', 'http://img1.qunarzz.com/sight/p0/1709/39/39b5b5a87f82aac2a3.img.jpg_r_800x800_5556a76a.jpg']
    }
  },
```
5. 设置点击banner打开画廊
+banner增加布尔值showGallery,点击时为true
+gallery增加点击事件,当点击时调用事件传给banner,banner调用事件控制showGallery为false

## banner头部
1. 返回为绝对定位 当向下滑动时隐藏
2. 头部为felx定位,当香香滑动显示
3. 头部滑动式奸淫剑仙效果
```
  data () {
    return {
      showAbs: true,
      styleObject: {    //在header绑定styleobject属性
        opacity: 0
      }
    }
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop  //当屏幕滚动式改变opacity值
      if (top > 40) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.styleObject = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)   //在activated生命周期里面进行  当页面展示的时候会执行
  }
  deactivated () {
    window.removeEventListener('scroll',this.handleScroll)   //deactivated时在页面隐藏或者切换的时候执行,如果不在这里清除window全局事件,那么在每一个页面都会执行这个函数
  }
```

##组件递归  在组件内部使用当前组件
1. 父组件中定义数据
```
  data () {
    return {
      list: [
        { title: '儿童票' ,
        children: [
          { title: '儿童1票' },
          { title: '儿童2票' },
          { title: '儿童3票' },
          { title: '儿童4票',children:[
            {title:'儿童儿子1'},
            {title:'儿童儿子2'},
            {title:'儿童儿子3'},
            {title:'儿童儿子4'}
          ] }
        ]},
        { title: '成人票' },
        { title: '老人票' },
        { title: '学生票' }
      ]
    }
  }
}
```
2. 子组件使用递归
```
  <div>
    <div
      v-for="(item, index) in List"
      :key="index"
      class="item"
    >
      <div class="item-title border-bottom"> {{item.title}} </div>
      <div v-if="item.children" class="item-children">
        <detail-list :List="item.children"></detail-list>          //用自己name实现递归
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
```
## 获取list页面数据
1. 通过axios获取数据
```
+第一种写法
  methods: {
    gitdetaileinfo () {
      axios.get('api/detail.json?id=' + this.$route.params.id).then(this.getdetailinfoSucc)
    },
+第二种
        gitdetaileinfo () {
      axios.get('api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.getdetailinfoSucc)
    },
```
2. 解决keepalive不会请求ajax的第二种方法
```
  <div id="app">
    <keep-alive exclude="detail">   //不自动请求缓存
      <router-view />
    </keep-alive>
  </div>
```
3. 解决切换路由页面跳转过去的页面没在最上面
```
 ],
  scrollBehavior (to, from, savedPosition) {   //路由里加上
    return {x: 0, y: 0}
  }
```
##banner加上动画
1. 在commom文件夹创建组件
```
<template>
  <transition>
    <slot></slot>
  </transition>
</template>
<script>
export default {
  name: 'animationFade'
}
</script>
<style lang="less" scoped>
.v-enter,
.v-leave-to {
  opacity: 0;
}
.v-enter-active,
.v-leave-active {
  transition: all.5s;
}
</style>
```
2. 在要使用动画的组件里引入动画组件,并注册然后直接用组件名称包裹要执行动画的组件
```
    <fade-animation>
      <detail-gallery
        :imgs="gallaryImgs"
        v-show="showGallery"
        @galleryClose="handleGalleryClose"
      ></detail-gallery>
    </fade-animation>
```




