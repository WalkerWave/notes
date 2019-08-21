## Vue路由

vue-router 是 Vue.js 官方的路由管理器，它和 Vue.js 的核心深度集成。

```html
<div id="app">
    <router-link to="/login">登录</router-link>
    <router-link to="/register">注册</router-link>
    <router-view></router-view>
</div>
<template id="login"></template>
<template id="register"></template>
<script>

var login = {
    template:'#login'
}
var register = {
    template:'#register'
}

var routerObj = new VueRouter({
    routers:[
        {path:'/',redirect:'/login'},
        {
            path:'/index',
            component:'index',
            children:[
                {path:'login',component:login},
                {path:'register',component:register}
            ]    
        }
    ]
})

var vm = new Vue({
    el:"#app",
    data:{},
    methods:{},
    router: routerObj  
})
</script>
```

+ 路由传参
```html
    <router-link to="/login?id=1"></router-link>
    <p>{{$route.query.id}}</p>
```
