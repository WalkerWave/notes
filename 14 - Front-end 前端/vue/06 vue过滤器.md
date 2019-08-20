### vue 过滤器

#### 字符串处理

```html
<div id="app">
    <p>{{ msg | sayHello }}</p>
</div>
<script>

    // 定义全局过滤器
    Vue.filter('sayHello',function(msg) {
        return 'Hello ' + msg
    })

    var vm = new Vue({
        el: '#app',
        data: {
            msg: 'vue.js'
        },
        methods: {}     
    })
</script>
```

#### 格式化时间

```html
<div id="app">
    <p>{{ date | dateFormat }}</p>
</div>
<script>

    // 定义全局过滤器 
    Vue.filter('dateFormat',function(dateStr) {
        var dt = new Date(dateStr)
        var y = dt.getFullYear()
        var m = (dt.getMonth + 1).toString().padStart(2,'0')
        var d = dt.getDate().toString().padStart(2,'0')
        var hh = dt.getHours().toString().padStart(2,'0')
        var mm = dt.getMinutes().toString().padStart(2,'0')
        var ss = dt.getSeconds().toString().padStart(2,'0') 
        // 使用字符串模板返回结果
        return `${y}-${m}-${d} ${hh}:${mm}:${ss}` 
    })

    var vm = new Vue({
        el: '#app',
        data: {
            date: new Date()
        },
        methods: {},
        filters: { // 定义局部过滤器 
            dateFormat: function(dateStr) {
                  var dt = new Date(dateStr)
                  var y = dt.getFullYear()
                  var m = (dt.getMonth() + 1).toString().padStart(2,'0')
                  var d = dt.getDate().toString().padStart(2,'0')                
                  // 使用字符串模板返回结果
                  return `${y}-${m}-${d}`
            }
        }   
    })
</script>
```

#### 按键修饰符

```html
<div id="app">
    <input type="text" @keyup.f2="sayHello"/>
</div>
<script>

    // 定义按键修饰符
    Vue.config.keyCodes.f2 = 113

    var vm = new Vue({
        el: '#app',
        data: {},
        methods: {
            sayHello(){
                console.log('hello')
            }
        }  
    })
</script>
```

+ 全局过滤器对所有的Vue实例都起作用
+ 如果全局过滤器和局部过滤器重名，优先调用局部过滤器
+ ES6字符串新方法使用padStart、padEnd来填充字符串