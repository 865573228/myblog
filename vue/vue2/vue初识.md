##### MVVM

- Model：负责数据存储
- View：负责页面展示
- View Model：负责业务逻辑处理（比如ajax请求等），对数据进行加工后交给视图展示

##### MVC模式（设计模式，前后端都有模式存在）

- M => model => 模型 => 数据（js变量）
- V => 试图 => 用户所见界面（html，css） 
- C => control => 控制器 => 事件交互 => 如何根据视图与用户交互后改变数据（通过DOM对象绑定事件，将变量进行修改）

##### 条件渲染

```html
<div v-if="isVip">用户类型：VIP用户</div>
<!-- <div>中间元素</div> -->   <!-- 注意v-if和v-else中间不能有其他的元素 -->
<div v-else-if="superVip">用户类型：超级VIP用户</div>
<div v-else>用户类型：普通用户</div>
```

!> v-show有较高的初始渲染成本，v-if有惰性，有较高的切换成本，所以频繁切换的时候用v-show比较好，但要从安全性能考虑的话就用v-if

##### 列表渲染

Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。这么做除了使 Vue 变得非常快之外，还有其它一些好处。例如，如果你允许用户在不同的登录方式之间切换：

```html
<template v-if="loginType === 'username'">
  <label>Username</label>
  <input placeholder="Enter your username">
</template>
<template v-else>
  <label>Email</label>
  <input placeholder="Enter your email address">
</template>
```

那么在上面的代码中切换 `loginType` 将不会清除用户已经输入的内容。因为两个模板使用了相同的元素，`<input>` 不会被替换掉——仅仅是替换了它的 `placeholder`。

只需添加一个具有唯一值的 `key` 在切换的时候就会清除用户已经输入的内容。

!> 注意我们不推荐在同一元素上使用 `v-if` 和 `v-for`。更多细节可查阅[风格指南](https://cn.vuejs.org/v2/style-guide/#避免-v-if-和-v-for-用在一起-必要)。当它们处于同一节点，`v-for` 的优先级比 `v-if` 更高，这意味着 `v-if` 将分别重复运行于每个 `v-for` 循环中。

##### 事件修饰符

- `.stop` 阻止冒泡（通俗讲就是阻止事件向上级DOM元素传递）。
- `.prevent` 阻止默认事件的发生。
- `.capture` 捕获冒泡，即有冒泡发生时，有该修饰符的dom元素会先执行，如果有多个，从外到内依次执行，然后再按自然顺序执行触发的事件。
- `.self` 将事件绑定到自身，只有自身才能触发，通常用于避免冒泡事件的影响
- `.once` 设置事件只能触发一次，比如按钮的点击等。
- `.passive` [.passive](https://www.cnblogs.com/llcdxh/p/10329414.html)该修饰符表示就是设置{passive:true}，表示处理事件函数中不会调用preventDefault函数，就会减少了额外的监听，从而提高了性能；所以不能和.prevent修饰符一同使用，否则浏览器会报错。
- `.native` 就是在父组件中给子组件绑定一个原生的事件，就将子组件变成了普通的HTML标签，不加'. native'事件是无法触 发的。

!> 使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 `v-on:click.prevent.self` 会阻止**所有的点击**，而 `v-on:click.self.prevent` 只会阻止对元素自身的点击。

!> 不要把 `.passive` 和 `.prevent` 一起使用，因为 `.prevent` 将会被忽略，同时浏览器可能会向你展示一个警告。请记住，`.passive` 会告诉浏览器你*不*想阻止事件的默认行为。

##### 表单输入绑定

```html
<div id="example-5">
  <select v-model="selected">
    <option disabled value="">请选择</option>
    <option v-for="item in items">{{item}}</option>
  </select>
</div>
```

!> 如果 `v-model` 表达式的初始值未能匹配任何选项，`<select>` 元素将被渲染为“未选中”状态。在 iOS 中，这会使用户无法选择第一个选项。因为这样的情况下，iOS 不会触发 change 事件。因此，更推荐像上面这样提供一个值为空的禁用选项。

- multiple  下拉框多选时需要加上这个属性，按着ctrl键就可以多选。

- 修饰符
  - .lazy  在默认情况下，`v-model` 在每次 `input` 事件触发后将输入框的值与数据进行同步，可以添加 `lazy` 修饰符，从而转为在 `change` 事件_之后_进行同步
  - .number  想自动将用户的输入值转为数值类型，可以给 `v-model` 添加 `number` 修饰符
  - .trim  如果要自动过滤用户输入的首尾空白字符，可以给 `v-model` 添加 `trim` 修饰符