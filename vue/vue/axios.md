axios

[axios安装教程](常用工具安装?=安装vuex&id=安装axios)

##### axios常见的请求方法

1. get（获取数据）

   ```js
   // 第一种写法
   axios.get('/data.json',{ // get带参数就写，不带就不写这个
     // http://8080/data.json?id=12
     params:{
       id:12
     }
   }).then(
   	(res) => {
   			console.log(res)
   	}
   )
   // 第二种别名方法
   axios({
     method:'get',
     url:'/data.json',
     params:{
       id:12
     }
   }).then(
   	(res) =>{
       	console.log(res)
     }
   )
   ```

2. post（提交数据【表单提交 + 文件上传】）

   ```js
   /* post常用的请求data格式有两种： 1. applicition/json（现在大部分用这个）   2. form-data 表单提交（文件、图片上传）*/
   // 1.applicition/json
   let data:{
     id:12
   }
   axios.post('/post',data).then(
   	(res) => {
       console.log(res)
     }
   )
   // 或者第二种别名方法
   axios({
     method:'post',
     url:'/post',
     data:data
   }).then(
   	(res) =>{
       console.log(res)
     }
   )
   // 2. form-data请求  以别名方法为例，第一种和上边第一种一样
   let formData = new FormData();
   for(let key in data){
     formData.append(key,data[key])
   }
   axios.post('/post',formData).then(
   	res => {
       console.log(res)
     }
   )
   ```

3. put（更新数据【所有的数据推送到后端】）

   ```js
   axios.put('/put',data).then(
   	res => {
       console.log(res)
     }
   )
   ```

4. patch（更新数据【只将修改的数据推送到后端】）

   ```js
   axios.patch('/put',data).then(
   	res => {
       console.log(res)
     }
   )
   ```

5. delete（删除数据）

   ```js
   // axios.delete(’url‘,config) 和get请求是类似的，只有两个参数， 而post、put、patch有三个参数
   // params
   axios.delete('delete',{
     params:{   // 这种写法参数直接在url后边显示，在Network里边的Query String Parameters中显示
       id:12
     }
   }).then(
     res=>{
     	console.log(res);
   })
   // data
   axios.delete('delete',{
     data:{    // 这种写法参数不会在url后边显示  而在Network里边的Request Payload中显示
       id:12
     }
   }).then(
     res=>{
     	console.log(res);
   })
   // 第二种
   axios({
     method:'delete',
     url:'/delete',
     params:{},  // 参数直接显示在url写法
     data:{}    //  参数不显示在url写法
   }).then(
     res=>{
     	console.log(res);
   })
   ```

##### 并发请求

- 并发请求：同时进行多个请求，并统一处理返回值

  ```js
  // axios.all()  参数是数组，数组里的值是一个一个的axios请求
  // axios.spread()  作用的在axios.all()多个请求完成之后把返回的数据进行分割处理
  axios.al(
  	[
    axios.get('/data.json'),
      axios.get('/city.json')
    ]
  ).then(
  	axios.spread(
    	(dataRes,cityRes) => {   // 上边有几个请求这里边就有几个返回值参数
        	console.log(dataRes,cityRes)
      }
    )
  )
  ```

##### 创建axios实例

- 后端接口地址有多个，并且超时时长不一样

  ```js
  let instance = axios.create({
    baseURL:'http://localhost:8080',
    timmeout:1000
  })
  let axios2 = axios.create({
    baseURL:'http://localhost:9090',
    timeout:2000
  })
  instance.get('/data.json').then(
  	res => {console.log(res)}
  )
  ```

##### axios基本配置参数

- axios配置参数

  ```js
  axios.create({
    baseURL:'http://localhost:8080',	//请求的域名，基本地址
    timeout:1000,	//请求超时时长（ms）
    url:'/data.json', 	// 请求路径
    method:'get',		// 请求方法
    headers:{
      token:''
    }, 		// 请求头
    params:{},	// 请求参数拼接在url上
    data:{},		// 请求参数放在请求体里
  })
  // 哪些地方可以进行参数配置？
  // 1.axios全局配置
  axios.defaults.timeout = 1000
  axios.defaults.baseURL = 'http://localhost:8080'			// defaults. 后边可以跟上边的哪些参数
  // 2.axios实例配置
  let instance = axios.create() // 不添加参数，实例的axios就是上边全局配置中的'http://localhost:8080'
  instance.degaults.timeout = 3000
  // 3.axios请求配置
  instance.get('/data.json',{
    timeout:5000
  })
  优先级：3 > 2 > 1
  ```

##### 拦截器

- 作用：在请求或响应被处理前拦截它们（就是在发起响应前处理，在响应之后处理）

  ```js
  // 分为两种：请求拦截器、响应拦截器、取消拦截器(不常用)
  // 1.请求拦截器
  axios.interceptors.request.use(config => {		// use()有两个参数，第一个参数是请求成功的回调函数，第二个就是请求错误的参数
  	// 在发送请求前做些什么
    return config
  },err => {
    // 在请求错误的时候做些什么
    return Promise.reject(err)
  })
  // 响应拦截器
  axios.interceptors.response.use(res => {
    // 请求成功对响应数据做处理
    return res   // 这个res请求成功后会回到axios.get().then(res =>{})中的res
  },err => {
    // 响应错误做些什么
    return Promise.reject(err)  // err会回到axios.get().then().catch(err =>{})中的err
  })
  // 取消拦截器
  let interceptors = axios.interceptors.request.use(config => {
    config.headers={
      auth:true
    }
    return config
  })
  axios.interceptors.request.eject(interceptors)
  ```

##### axios错误处理

- 作用：请求错误时进行的处理

  ```js
  axios.get('/data.json').then(
  	(res) => {
      console.log(res)
    }).catch( err => {
    	console.log(err)
  })
  // 例子：实际开发中，一般添加统一的错误处理
  let instance = axios.create({})
  instance.interceptors.request(config => {
    return config
  },err => {
    //请求错误 一般http状态码以4开头，常见：401超时，404 not found
    retunr Promise.reject(err)
  })
  instance.interceptors.response.use(res => {
    return res
  },err => {
    // 响应错误处理 一般http状态码以5开头，常见的500 系统错误，502系统重启
    return Promise.reject(err)
  })
  ```

##### axios取消请求

- 作用：用于取消正在进行的http请求（了解）

  ```js
  let source = axios.CancelToken.source()
  axios.get('/data.json',{
    cancelToken:source.token
  }).then(res => {
    console.log(res)
  }).catch(
  err => {
    console.log(err)
  })
  // 取消请求
  source.cancel('cancel http') // 参数可选，会传到catch()里边
  ```

  