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
3. git pust 提交到github分支
4. git checkout master 切换到主分支
5. git merge origin/dev 把线上的dev分支合并到主分支
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



