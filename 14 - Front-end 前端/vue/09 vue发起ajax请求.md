## vue-resource发起get、psot、jsonp请求
```javascript
      // GET /someUrl?foo=bar
      this.$http.get('/someUrl', {params: {foo: 'bar'}}).then(response => {
        // success callback
      }, response => {
        // error callback
      });
    
      // JSONP /someUrl?foo=bar
      this.$http.jsonp('/someUrl', {params: {foo: 'bar'}}).then(response => {
        // success callback
      }, response => {
        // error callback
      });
    
      // POST /someUrl
      this.$http.post('/someUrl', {foo: 'bar'}).then(response => {
    
        // get status
        response.status;
    
        // get status text
        response.statusText;
    
        // get 'Expires' header
        response.headers.get('Expires');
    
        // get body data
        this.someData = response.body;
    
      }, response => {
        // error callback
      });
```

##  Axios发起get、post请求

```javascript
    // 一、执行 GET 请求
    
    // 为给定 ID 的 user 创建请求
    axios.get('/user?ID=12345')
    .then(function (response) {
        console.log(response);
    })
    .catch(function (error) {
        console.log(error);
    });
    
    // 可选地，上面的请求可以这样做
    axios.get('/user', {params: {ID: 12345}})
    .then(function (response) {
        console.log(response);
    })
    .catch(function (error) {
        console.log(error);
    });
    
    // 二、执行 POST 请求
    
    axios.post('/user', {
        firstName: 'Fred',
        lastName: 'Flintstone'
    })
    .then(function (response) {
        console.log(response);
    })
    .catch(function (error) {
        console.log(error);
    });
    
    // 三、执行多个并发请求
    
    function getUserAccount() {
      return axios.get('/user/12345');
    }
    
    function getUserPermissions() {
      return axios.get('/user/12345/permissions');
    }
    
    axios.all([getUserAccount(), getUserPermissions()])
    .then(axios.spread(function (acct, perms) {
        // 两个请求现在都执行完成
    }));
```
