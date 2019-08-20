## v-for 指令学习

1、遍历数组
```html
<div id="app">
    <p v-for="(item,i) in fruits">{{item}}}</p>
    <p v-for="(item,i) in students">name：{{item.name}}} --- age：{{item.age}}</p>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
           fruits: ['apple','banana','orange'],
           students: [
            {name: 'tony',age: 21,gender: 'man'},
            {name: 'Leo',age: 23,gender: 'man'},
            {name: 'cindy',age: 21,gender: 'woman'}
           ]
        }
        methods: {}     
    })
</script>
```

2、遍历对象
```html
<div id="app">
    <p v-for="(val,key) in tony">{{key}}：{{val}}</p>
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            tony: {
                name: 'tony'        
                age: 21,
                gender: 'man'
            }
        },
        methods: {}     
    })
</script>
```

* 在组件中使用v-for时，需要选择唯一的字符串或数字作为key值！！！
```html
<div id="app">
    <p v-for="(item,i) in students" :key="item.id">
        <input type="checkbox"/>{{item.name}} 
    </p>
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
        methods: {}     
    })
</script>
```