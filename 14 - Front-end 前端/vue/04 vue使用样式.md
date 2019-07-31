### vue 使用样式

+ class 样式

```html
<style>
    .red {
        color:red;
    }
    .thin {
        font-weight: 200;
    }
</style>
```
1、数组
```html
    <h3 :class="['red','thin']">Hello vue.js !!! </h3>
```

2、数组中使用三元表达式
```html
<div id="app">
    <h3 :class="['red', isTHin ? 'thin' : '']">Hello vue.js !!! </h3>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            isTHin: true
        },
        methods: {}     
    })
</script>
```

3、数组中嵌套对象
```html
<div id="app">
    <h3 :class="['red', {'thin':isThin}]">Hello vue.js !!! </h3>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            isTHin: true
        },
        methods: {}     
    })
</script>
```

4、对象
```html
<div id="app">
    <h3 :class="{red: true,thin: isTHin}">Hello vue.js !!! </h3>
    <h3 :class="classObj">Hello vue.js !!! </h3>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            isTHin: true,
            classObj: {red: true,thin: true}
        },
        methods: {}     
    })
</script>
```

+ 内联样式

1、样式对象
```html
<div id="app">
    <h3 :style="{color: 'red','font-weight': 200}">Hello vue.js !!! </h3>
    <h3 :style="styleObj">Hello vue.js !!! </h3>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            styleObj: {color: 'red','font-weight': 200}
        },
        methods: {}     
    })
</script>
```

2、数组
```html
<div id="app">
    <h3 :style="[styleObj1,styleObj2]">Hello vue.js !!! </h3>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            styleObj1: {color: 'red','font-weight': 200},
            styleObj2: {color: 'red','font-weight': 200}
        },
        methods: {}     
    })
</script>
```




