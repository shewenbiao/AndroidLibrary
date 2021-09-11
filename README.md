# AndroidLibrary
Android主流的一些第三方库，常用插件，技术网站，技术公众号等

## 网络库
| 主流框架            | 介绍      | 特点  | 优点  | 缺点  | 官网或相关地址 |
|:-------------------|:----------|:----------|:----------|:----------|:----------|
| OkHttp             | Square公司出品，一个高效，高性能的http请求库 。  | 1.使用连接池来复用连接以提供效率<br>2.支持SPDY,共享同一个Socket来处理同一个服务器所有的请求<br>3.支持http2.0、Websocket<br>4.支持同步、异步执行<br>5.封装线程池、数据转换、参数使用、错误处理等<br>6.无缝支持Gzip来减少数据流量<br>7.缓存响应数据来减少重复的网络请求<br>8.能从很多常用的连接问题中自动恢复<br>9.解决了代理服务器问题和SSL握手失败问题| 拥有Nio和Okio，所以性能更高，请求、处理速度更快（io:阻塞式 nio：非阻塞式）|   | https://github.com/square/okhttp        |
| Retrofit           | Square公司出品，适用于 Android 和 Java 的类型安全 HTTP 客户端。基于注解。底层分装了OkHttp。  |1.Resrful api设计风格<br>2.支持同步、异步<br>3.通过注解配置请求，包括请求方法、参数、请求头、返回值等<br>4.可以搭配多种Converter将获得数据解析&序列化<br>5.支持Gson（默认）、Jsckson、Protobuf等<br>6.提供Rxjava支持 | 代码简化，结构彻底，职责细分；易于和rxjava使用    |     | https://github.com/square/retrofit      |
| android-async-http | Google推出的一个基于 Apache 的 HttpClient 库的 Android 异步、基于回调的 Http 客户端。    |1.基于HttpClient<br>2.在UI线程外、异步进行http请求<br>3.在匿名回调中处理请求结果，callback使用了Andorid的Handler发送消息机制在创建它的线程中执行<br>4.自动智能请求重试机制<br>5.持久化cookie存储，保存cookit到应用程序的SharedPreferences|   |  | https://github.com/loopj/android-async-http <br> http://loopj.com/android-async-http/ |
| Volley             | Google推出的异步网络请求框架。特别适合数据量小，通信频繁的网络操作。  |1.基于HttpUrlConnection,封装了UIL图片加载框架，支持图片加载<br>2.网络请求的排序、优先级处理缓存<br>3.多级别取消请求<br>4.Activity和生命周期的联动（Activity结束生命周期同时取消所有网络请求）| 拓展性好，可支持httpClient、HTTPURLConnection、okhttp    | 只适合小数据传输  | https://github.com/google/volley   |


Android6.0以后Google官方Api移除HttpClient，继续使用HttpClient及基于其封装的网络库(例如android-async-http）会出异常, 需要在build.gradle里添加
```java
android {
    useLibrary ‘org.apache.http.legacy’
}
```


另外还有国内开发者开发的一些网络库（[xUtils](https://github.com/wyouflf/xUtils3), [NoHttp](https://github.com/wyouflf/xUtils3), [afinal](https://github.com/yangfuhai/afinal) 等)，不过大部分许久未更新，已经不维护了，不推荐使用。


**主流使用方式：** OkHttp + Retrofit


## 图片加载库
| 主流框架                        | 介绍       | 优点       | 缺点  |  官网或相关地址 |
|:-------------------------------|:----------|:----------|:----------|:----------|
| Glide                          | Google出品的图片加载框架，基于Picasso，和Picasso一样使用简洁    | 1. 功能强大并且使用简洁 <br> 2. Bitmap 格式是 RGB_565 格式, 内存消耗少 <br> 3. 存储是动态的，是根据屏幕控件大小，来缓存对应尺寸的图片到本地内存，节省存储空间、加载速度也变快 <br> 4. 支持Gif    |     | https://github.com/bumptech/glide    |
| Picasso                        | Square公司开源的一个Android平台上的图片加载框架，简单易用    | 功能强大并且使用简洁    | 1. 不支持Gif <br> 2. Bitmap 格式是ARGB_8888 格式，相对耗内存 <br> 3. 只会缓存原始尺寸的图片, 因此加载速度比glide慢  | https://github.com/square/picasso    |
| Fresco                         |  Facebook 出品的图片加载框架    | 1. 在Native层优化内存，避免OOM出现 <br> 2. 加载大图时，有的图Glide和Picasso加载不出来，Fresco可以    | 使用相对麻烦，导入包体积大   | https://github.com/facebook/fresco    |
| Android-Universal-Image-Loader | 比较老的图片加载库，现在已经停止维护。不建议使用。   |     |     | https://github.com/nostra13/Android-Universal-Image-Loader    |

