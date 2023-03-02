### reactive

和ref区别

1. ref 支持所有类型

    reactive 只支持引用类型：Array、Object、Map、Set

2. ref取值赋值都需要.value，reactive不需要

``` js
import { reactive } from "vue"
type M = {
  name?: string,
  age?: number
}
const a = reactive<M>({
  name: "ceshi",
  age: 12
})
```
