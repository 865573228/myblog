##### 生命周期

```js
 // 创建 Vue 实例，得到 ViewModel
17     var vm = new Vue({
18       el: '#app',
19       data: {
20         msg: 'ok'
21       },
22       methods: {
23         show() {
24           console.log('执行了show方法')
25         }
26       },
27       beforeCreate() {
28         this.show()
29         // 这是第一个生命周期函数，表示实例完全被创建出来之前，会执行它
30         // console.log(this.msg)
31         // 注意：在beforeCreate生命周期函数执行的时候，data和methods中的数据都还没有没初始化
32       },
33       created() {
34         // 这是第二个生命周期函数
35         // console.log(this.msg)
36         // this.show()
37         // 在 created 中，data 和 methods 都已经被初始化好了！
38         // 如果要调用methods中的方法，或者操作 data 中的数据，最早只能在 created 中操作
39       },
40       beforeMount() {
41         // 这是第3个生命周期函数，表示模板已经在内存中编辑完成了，但是尚未把 模板渲染到 页面中
42         // console.log(document.getElementById('h3').innerText)
43         // 在 beforeMount 执行的时候，页面中的元素，还没有被真正替换过来，只是之前写的一些模板字符串
44       },
45       mounted() {
46         // 这是遇到的第4个生命周期函数，表示，内存中的模板，已经真实的挂载到了页面中，用户已经可以看到渲染好的页面了
47         // console.log(document.getElementById('h3').innerText)
48         // 注意：mounted是实例创建期间的最后一个生命周期函数，当执行完mounted就表示，实例已经被完全创建好了
49       },
50 
51       // 接下来的是运行中的两个事件
52       beforeUpdate() { 
53         // 这时候，表示 我们的界面还没有被更新【数据被更新了吗？  数据肯定被更新了】
54         /* console.log('界面上元素的内容：' + document.getElementById('h3').innerText)
55         console.log('data 中的 msg 数据是：' + this.msg) */
56         // 得出结论： 当执行beforeUpdate的时候，页面中的显示的数据，还是旧的，此时data数据是最新的，页面尚未和最新的数据保持同步
57       },
58       updated() {
59         console.log('界面上元素的内容：' + document.getElementById('h3').innerText)
60         console.log('data 中的 msg 数据是：' + this.msg)
61         // updated 事件执行的时候，页面和 data 数据已经保持同步了，都是最新的
62       },
63       beforeDestroy() {
64 
65       },
66       destroyed() {
67 
68       }
69     });
```

![生命周期图片](../../imgs/lifecycle.png)

