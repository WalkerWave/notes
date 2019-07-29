### vue 指令学习

    解决插值表达式闪烁问题
    
###
 ```html
 <style>
    [v-cloak]{
        display: none;
    }
</style>
 <div id="app">
     <p v-cloak>hello {{ msg }}</p>
     <!-- 插值表达式只会替换自己，不会清空元素中其他内容 -->
     <p v-text="msg">hello</p>
     <!-- v-test 不存在闪烁问题，会覆盖元素中的内容 -->
     <p v-html="msgs">hello</p>
     <!-- v-html 将内容当做html进行解析 -->
     <input type="button" v-bind:title="msgs" v-on:click="sayHello">hello</input>
     <!-- v-bind 用于绑定属性 简写为 :title="表达式" -->
     <!-- v-on 用于绑定事件 简写为 @click="方法名" -->
 </div>
 <script>
     // 创建Vue实例
     var vm = new Vue({
         el: '#app', // 表示要操作的页面元素
         data: {     // 存放元素中用到的数据
             msg: 'Vue.js',
             msgs: '<h1>Vue.js</h1>'
         },
         methods:{
             sayHello: function(){
                 alert('Hello');
             }
         }
     })
 </script>
    