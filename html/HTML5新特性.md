##### HTML5新特性

- 语义标签

  |          标签           |               描述               |
  | :---------------------: | :------------------------------: |
  |   `<header></header>`   |       定义了文档的头部区域       |
  |   `<footer></footer>`   |       定义了文档的尾部区域       |
  |      `<nav></nav>`      |          定义文档的导航          |
  |  `<section></section>`  | 定义文档中的节（section、区段）  |
  |  `<article></article>`  |      定义页面独立的内容区域      |
  |    `<aside></aside>`    |       定义页面的侧边栏内容       |
  | `<detailes></detailes>` | 用于描述文档或文档某个部分的细节 |
  |  `<summary></summary>`  |   标签包含 details 元素的标题    |
  |   `<dialog></dialog>`   |      定义对话框，比如提示框      |

- 增强型表单

  - 　HTML5 拥有多个新的表单 Input 输入类型。这些新特性提供了更好的输入控制和验证。

  |    输入类型    |             描述             |
  | :------------: | :--------------------------: |
  |     color      |       主要用于选取颜色       |
  |      date      | 从一个日期选择器选择一个日期 |
  |    datetime    |   选择一个日期（UTC 时间）   |
  | datetime-local | 选择一个日期和时间 (无时区)  |
  |     email      |   包含 e-mail 地址的输入域   |
  |     month      |         选择一个月份         |
  |     number     |         数值的输入域         |
  |     range      |   一定范围内数字值的输入域   |
  |     search     |          用于搜索域          |
  |      tel       |     定义输入电话号码字段     |
  |      time      |         选择一个时间         |
  |      url       |       URL 地址的输入域       |
  |      week      |          选择周和年          |

  - HTML5 也新增以下表单元素

  |   输入类型   |                             描述                             |
  | :----------: | :----------------------------------------------------------: |
  | `<datalist>` | 元素规定输入域的选项列表<br />使用 `<input>` 元素的 list 属性与 `<datalist>`  元素的 id 绑定 |
  |  `<keygen>`  | 提供一种验证用户的可靠方法，标签规定用于表单的密钥对生成器字段。 |
  |  `<output>`  |            用于不同类型的输出，比如计算或脚本输出            |

  - HTML5 新增的表单属性

    - placehoder 属性，简短的提示在用户输入值前会显示在输入域上。
    - required  属性，是一个 boolean 属性。要求填写的输入域不能为空
    - pattern 属性，描述了一个正则表达式用于验证 `<input>` 元素的值。
    - min 和 max 属性，设置元素最小值与最大值。
    - step 属性，为输入域规定合法的数字间隔。
    - height 和 width 属性，用于 image 类型的 `<input>`  标签的图像高度和宽度。
    - autofocus 属性，是一个 boolean 属性。规定在页面加载时，域自动地获得焦点。
    - multiple 属性 ，是一个 boolean 属性。规定`<input>`  元素中可选择多个值。

- 视频和音频

  - 视频 `<video>`

  ```html
  <video width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.ogg" type="video/ogg">
  您的浏览器不支持Video标签。 
  </video>
  <!--标签之间插入的内容是提供给不支持 video 元素的浏览器显示的。-->
  <!--浏览器将使用第一个可识别的格式（ MP4, WebM, 和 Ogg）-->
  ```

  - 音频 `<audio>`

  ```html
  <audio controls>
    <source src="horse.ogg" type="audio/ogg">
    <source src="horse.mp3" type="audio/mpeg">
  您的浏览器不支持 audio 元素。
  </audio>
  <!--标签之间插入的内容是提供给不支持 audio 元素的浏览器显示的。-->
  <!--支持三种音频格式文件: MP3, Wav, 和 Ogg-->
  ```

- Canvas绘图

  - canvas和svg区别
    - SVG 是一种使用 XML 描述 2D 图形的语言。
    - Canvas 通过 JavaScript 来绘制 2D 图形。
    - SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器。
    - 在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。
    - Canvas 是逐像素进行渲染的。在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。

- 地理定位

  HTML5 Geolocation（地理定位）用于定位用户的位置。

```js
window.navigator.geolocation {
    getCurrentPosition:  fn  用于获取当前的位置数据
    watchPosition: fn  监视用户位置的改变
    clearWatch: fn  清除定位监视
}　　　
// 获取用户信息
navigator.geolocation.getCurrentPosition(
    function(pos){
　　　　console.log('用户定位数据获取成功')
　　　　//console.log(arguments);
　　　　console.log('定位时间：',pos.timestamp)
　　　　console.log('经度：',pos.coords.longitude)
　　　　console.log('纬度：',pos.coords.latitude)
　　　　console.log('海拔：',pos.coords.altitude)
　　　　console.log('速度：',pos.coords.speed)

},    //定位成功的回调
function(err){ 
　　　　console.log('用户定位数据获取失败')
　　　　//console.log(arguments);
	}    //定位失败的回调
)
```

- 拖放API

  - 拖放的源对象(可能发生移动的)可以触发的事件——3个：

    1. dragstart：拖动开始

    2. drag：拖动中

    3. dragend：拖动结束

       整个拖动过程的组成： dragstart*1 + drag*n + dragend*1

  - 拖放的目标对象(不会发生移动)可以触发的事件——4个：

    1. dragenter：拖动着进入

    2. dragover：拖动着悬停

    3. dragleave：拖动着离开

    4. dragleave：拖动着离开

       整个拖动过程的组成1： dragenter*1 + dragover*n + dragleave*1

       整个拖动过程的组成2： dragenter*1 + dragover*n + drop*1

  - dataTransfer：用于数据传递的“拖拉机”对象；

    -  在拖动源对象事件中使用e.dataTransfer属性保存数据：

      ```js
      e.dataTransfer.setData( k,  v )
      ```

    - 在拖动目标对象事件中使用e.dataTransfer属性读取数据：

      ```js
      var value = e.dataTransfer.getData( k )
      ```

- Web Worker

  - 当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。

  - web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。

  - 首先检测浏览器是否支持 Web Worker

    ```js
    if(typeof(Worker)!=="undefined"){
      // 是的! Web worker 支持!
      // 一些代码.....
      }else{
      // //抱歉! Web Worker 不支持
      }
    // 下面的代码检测是否存在 worker，如果不存在，- 它会创建一个新的 web worker 对象，然后运行 "demo_workers.js" 中的代码
    if(typeof(w)=="undefined")
      {
      w=new Worker("demo_workers.js");
      }
    // 然后我们就可以从 web worker 发送和接收消息了。向 web worker 添加一个 "onmessage" 事件监听器：
    w.onmessage=function(event){
    document.getElementById("result").innerHTML=event.data;
    };
    
    ```

    当 web worker 传递消息时，会执行事件监听器中的代码。event.data 中存有来自 event.data 的数据。当我们创建 web worker 对象后，它会继续监听消息（即使在外部脚本完成之后）直到其被终止为止。

    如需终止 web worker，并释放浏览器/计算机资源，使用 terminate() 方法。

- Web Storage

  在使用 web 存储前,应检查浏览器是否支持 localStorage 和sessionStorage

  ```js
  if(typeof(Storage)!=="undefined")
     {
     // 是的! 支持 localStorage  sessionStorage 对象!
     // 一些代码.....
     }
   else
     {
     // 抱歉! 不支持 web 存储。
     }
  ```

  不管是 localStorage，还是 sessionStorage，可使用的API都相同，常用的有如下几个（以localStorage为例）：

  - 保存数据：localStorage.setItem(key,value);
  - 读取数据：localStorage.getItem(key);
  - 删除单个数据：localStorage.removeItem(key);
  - 删除所有数据：localStorage.clear();
  - 得到某个索引的key：localStorage.key(index);

- WebSocket

  WebSocket是HTML5开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。在WebSocket API中，浏览器和服务器只需要做一个握手的动作，然后，浏览器和服务器之间就形成了一条快速通道。两者之间就直接可以数据互相传送。浏览器通过 JavaScript 向服务器发出建立 WebSocket 连接的请求，连接建立以后，客户端和服务器端就可以通过 TCP 连接直接交换数据。当你获取 Web Socket 连接后，你可以通过 **send()** 方法来向服务器发送数据，并通过 **onmessage** 事件来接收服务器返回的数据。

  ```js
  <!DOCTYPE HTML>
  <html>
     <head>
     <meta charset="utf-8">
     <title>W3Cschool教程(w3cschool.cn)</title>
        <script type="text/javascript">
           function WebSocketTest()
           {
              if ("WebSocket" in window)
              {
                 alert("您的浏览器支持 WebSocket!");
                 // 打开一个 web socket
                 var ws = new WebSocket("ws://localhost:9998/echo");
                 ws.onopen = function()
                 {
                    // Web Socket 已连接上，使用 send() 方法发送数据
                    ws.send("发送数据");
                    alert("数据发送中...");
                 };
                 ws.onmessage = function (evt) 
                 { 
                    var received_msg = evt.data;
                    alert("数据已接收...");
                 };
                 ws.onclose = function()
                 { 
                    // 关闭 websocket
                    alert("连接已关闭..."); 
                 };
              }
              else
              {
                 // 浏览器不支持 WebSocket
                 alert("您的浏览器不支持 WebSocket!");
              }
           }
        </script>
     </head>
     <body>
        <div id="sse">
           <a href="javascript:WebSocketTest()">运行 WebSocket</a>
        </div>
     </body>
  </html>
  ```

  

