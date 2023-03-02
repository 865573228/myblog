### vscode 提示：找不到模块“./*.vue”或其相应的类型声明。ts()

在项目根目录创建 env.d.ts 文件（如果已有，则在文件中追加），加入以下内容：

``` vue
declare module "*.vue" {
  import type { DefineComponent } from "vue"; 
  const vueComponent: DefineComponent<{}, {}, any>; 
  export default vueComponent;
}
```
