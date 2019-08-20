## vue 指令学习

  v-cloak  解决插值表达式闪烁问题

  v-text 以字符串形式设置元素内容

  v-html 以html方式设置元素内容

  v-bind 为元素绑定属性

  v-on 为元素绑定事件

  v-model 实现数据的双向绑定

  v-if 判断是否创建或者删除元素

  v-show 判断是否显示或者隐藏元素
  
 ```html
 <style>
    [v-cloak]{
        display: none;
    }
</style>
     <!-- 插值表达式只会替换自己，不会清空元素中其他内容 -->
     <p v-cloak>hello {{ msg }}</p>

     <!-- v-test 不存在闪烁问题，会覆盖元素中的内容 -->
     <p v-text="msg">hello</p>

     <!-- v-html 将内容当做html进行解析 -->
     <p v-html="msgs">hello</p>

     <!-- v-bind 用于绑定属性 简写为 :title="表达式" -->
     <!-- v-on 用于绑定事件 简写为 @click="方法名" -->
     <input type="button" v-bind:title="msgs" v-on:click="sayHello">hello</input>

     <!-- v-model 用于实现数据的双向绑定 -->
     <input type="text" v-model="msg"/>

     <!-- v-if 用于是否创建或者删除元素 -->
     <input type="text" v-if="isExist"/>

     <!-- v-show 用于是否显示或者隐藏元素 -->
     <input type="text" v-show="isShow"/>
 </div>
 <script>
     // 创建Vue实例
     var vm = new Vue({
         el: '#app', // 表示要操作的页面元素
         data: {     // 存放元素中用到的数据
             msg: 'Vue.js',
             msgs: '<h1>Vue.js</h1>',
             isExist: true,
             isShow: false
         },
         methods:{
             sayHello: function(){
                 alert('Hello');
             }
         }
     })
 </script>
 ```

 ## 事件修饰符

 stop 阻止冒泡

 prevent 阻止默认事件

 capture 添加事件侦听器时使用事件捕获机制

 self 只当事件在该元素本身触发时触发回调

 once  事件只触发一次
