## VUE
    vue.js 是一套构建用户界面的前端框架，和Angular.js,React.js并称为三大主流框架。

## MVVM

MVVM 前端视图层的概念，主要关注视图层分离，即Model（数据）,View（HTML结构）,VM ViewModel（数据双向绑定）。

```html
<div id="app">
    <p>{{ msg }}</p>
</div>
<script>
    // 创建Vue实例
    var vm = new Vue({
        el: '#app', // 表示要操作的页面元素
        data: {     // 存放元素中用到的数据
            msg: 'hello Vue.js'
        }
    })
</script>
```






