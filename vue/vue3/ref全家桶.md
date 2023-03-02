### ref

接受一个内部值并返回一个响应式且可变的 ref 对象。ref 对象仅有一个 .value property，指向该内部值。

``` vue
<script setup lang="ts">
  import { ref } from 'vue';
  type M = {
    name: string
  }
  const a = ref<M>({ name: '测试' })
  const b = ref<number>(123)
  const changeBtn = () => {
    a.value.name = "修改后的"
    b.value = -10
  }
</script>
```

### idRef

判断是不是一个ref对象

``` vue
<script setup lang="ts">
  import { ref, Ref,isRef } from 'vue'
  let message: Ref<string | number> = ref("我是message")
  let notRef:number = 123
  const changeMsg = () => {
    message.value = "change msg"
    console.log(isRef(message)); //true
    console.log(isRef(notRef)); //false
  }
</script>
```

### shallowRef

创建一个跟踪自身 .value 变化的 ref，但不会使其值也变成响应式的(浅层响应式)

``` js
import { ref, shallowRef } from 'vue'
// 1 会变化
const a = shallowRef(1)
const changeBtn = ()=>{
  a.value = 2
}
// 2 不会变化
const a = shallowRef({age:10})
const changeBtn = ()=>{
  a.value.age = 20
}
// 3 会变化 有其他的ref一块就会变化
const b = ref(1)
const a = shallowRef({age:10})
const changeBtn = ()=>{
  b.value = 2
  a.value.age = 20
}
```
