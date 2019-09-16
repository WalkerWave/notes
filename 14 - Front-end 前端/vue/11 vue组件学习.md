## 定义vue组件

组件的出现，就是为了拆分vue实例的代码量，能够以不同的组件，划分不同的功能，当我们需要什么样的功能，就去调用对应的组件即可。

### 组件化和模块化

   + 模块化：是从代码逻辑角度进行划分的，方便代码分层开发，保证每个功能模块只能单一；
   + 组件化：是从UI界面的角度进行划分的，方便页面进行重用；

### 定义全局组件
```html
<div id="app">
    <my-com1></my-com1>
    <my-com2></my-com2>
    <my-com3></my-com3>
</div>
<template id="temp">
    <h3>Vue创建全局{{msg}}组件</h3>
</template>
<script>
    // 1、myCom1
    // 使用Vue.extend创建全局Vue组件模板
    var com = Vue.extend({
        template: '<h3>Vue创建全局Vue组件</h3>'
    })
    // 使用Vue.component('组件名称','组件模板名称')注册组件
    Vue.component('MyCom1',com);  

    // 也可简写为如下
    Vue.component('MyCom1',Vue.extend({
        template: '<h3>Vue创建全局Vue组件</h3>'
    }));  

    // 2、myCom2
    Vue.component('MyCom2',{
        template: '<h3>Vue创建全局Vue组件</h3>'
    });

    // 3、myCom3
    Vue.component('MyCom3',{
        template: '#temp',
        date(){
            return {
                msg:'Vue'
            }
        },
        methods: {}
    })

    var vm = new Vue({
        el: '#app',
        data: {},
        methods: {}  
    })
</script>
```

### 定义私有组件
```html
<div id="app">
    <my-com1></my-com1>
    <my-com2></my-com2>
    <!-- component 用于展示对应名称组件，一般用于多组件切换 -->
    <component :is="'MyCom1'"></component>
</div>

<template id="temps">
    <h3>Vue创建私有Vue组件</h3>
</template>
<script>
    var vm = new Vue({
        el: '#app',
        data: {},
        methods: {},
        components:{  
            myCom1: {
                template:'<h3>Vue创建私有Vue组件</h3>'
            },
            myCom2: {
                template:'#temps'
            }
        }
    })
</script>
```

### 父组件通过数据绑定向子组件传值
```html
<div id="app">
    <my-com :parentMsg="msg"></my-com>
</div>

<template id="temps">
    <h3>{{parentMsg}} {{today}}</h3>
</template>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg:'hello'
        },
        methods: {},
        components:{  
            MyCom: {
                props:['parentMsg'],
                template:'#temps',
                data(){
                    return{
                        today:new Date()
                    }
                }
            }
        }
    })
</script>
```

### 子组件通过事件调用向父组件传值
```html
<div id="app">
    <my-com @show-msg="showMsg"></my-com>
</div>

<template id="temps">
    <button @click="send">button</button>
</template>
<script>
 var vm = new Vue({
    el: '#app',
    data: {
        msg:'hello'
    },
    methods: {
        showMsg(msg){
            console.log(msg)
        }
    },
    components:{  
        MyCom: {
            props:['parentMsg'],
            template:'#temps',
            data(){
                return{
                    today:new Date()
                }
            },
            methods: {
                send(){
                    this.$emit('show-msg',this.today)                    
                }
            }
        }
    }
})
</script>
```

### 父、子组件数据双向绑定
```html
<div id="app">
    <my-com v-model="msg"></my-com>
</div>

<template id="temps">
    <input :value="value" @input="change" type="text"/>
</template>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg:'hello'
        },
        methods: {},
        components:{  
            myCom: {
                props:['value'],
                template:'#temps',
                data(){
                    return{}
                },
                methods: {
                    change(){
                        this.$emit('input',$event.target.value)                    
                    }
                }
            }
        }
    })
</script>
```

+ 组件template模板只能有且仅有唯一的根元素
