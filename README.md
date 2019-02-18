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


