## vue 实例的生命周期

从vue实例创建、运行、到销毁期间，总是伴随着各种各样的事件，这些事件统称为生命周期。

### 创建阶段

beforeCreate 在vue实例创建之前执行

created 在vue实例创建成功之后执行

beforeMount 当模板在内存中编译完成，尚未渲染到页面中时执行

mounted 在内存中的模板渲染到页面之后执行，此时vue实例初始化完毕

### 运行阶段

beforeUpdate data中数据被更新但界面中还未更新时执行  

updated data中数据被更新且页面中重新渲染完毕时执行

### 销毁阶段

beforeDestroy vue实例彻底销毁之前执行

destroyed vue实例彻底销毁后执行
