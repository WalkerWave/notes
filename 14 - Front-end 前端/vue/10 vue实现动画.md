## vue实现动画

+ 过度类名实现动画

```html
<style>

    /*
    动画进入之前、离开之后
    */
    .v-enter,
    .v-leave-to{
        opacity: 0;
    }
    
    /*
     动画进入、离开期间
     */
    .v-enter-active,
    .v-leave-active{
        transition: all 0.5s ease;
    }
</style>
<div id="app">
    <!-- mode 属性用于设置动画切换模式 -->
    <transition mode="out-in">
        <p>{{msg}}</p>
    </transition>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg: 'vue.js'
        },
        methods: {}
    })
</script>
```

+ 自定义类名实现动画

```html
<style>

    .tx-enter,
    .tx-enter-to{
        opacity: 0;
    }
    
    .tx-enter-active,
    .tx-leave-active{
        transition: all 0.5s ease;
    }
</style>
<div id="app">
    <transition name="tx">
        <p>{{msg}}</p>
    </transition>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg: 'vue.js'
        },
        methods: {}
    })
</script>
```

+ 使用第三方类库实现动画
```html
<link rel="stylesheet" href="./lib/animate.css">
<div id="app">
    <transition enter-active-class="bounceIn" leave-active-class="bounceOut" 
        :duration="{enter: 300,leave: 100}">
        <p class="animated">{{msg}}</p>
    </transition>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg: 'vue.js'
        },
        methods: {}
    })
</script>
```

+ 使用钩子函数创建动画
```html
<div id="app">
    <transition 
        @before-enter="beforeEnter"
        @enter="enter"
        @after-enter="afterEnter">
        <p>{{msg}}</p>
    </transition>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg: 'vue.js'
        },
        methods: {
            beforeEnter(el) {
                //设置style
            },
            enter(el,done){
                //设置style
                done();
            },
            afterEnter(el){
                //设置style
            }
        }
    })
</script>
```
+ transition-group实现列表动画
```html
<style>
    p{
        border:1px dashed #999;
        margin: 5px;
    }
    v-enter,
    v-leave-to{
        opacity: 0;
    }
    
    v-enter-active,
    v-leave-active{
        transition: all 0.5s ease;
    }
    
    v-move{
        transition: all 0.5s ease;
    }
    v-leave-active{
        position: absolute;
    }
</style>
<div id="app">
    <!-- appear 页面初始渲染时使用动画 -->
    <!-- tag 指定transition-group渲染为指定元素，默认为span -->
    <transition-group appear tag="div"> 
        <p v-for="(item,i) in students" :key="item.id" @click="delete(i)">{{item.name}}</p>
    </transition-group>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
             students: [
                {name: 'tony',id: 1,gender: 'man'},
                {name: 'Leo',id: 2,gender: 'man'},
                {name: 'cindy',id: 3,gender: 'woman'} 
             ]
        },
        methods: {
            delete(i) {
                this.students.splice(i,1);
            }
        }
    })
</script>
```