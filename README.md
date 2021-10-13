# AndroidLibrary
Android主流的一些第三方库，Android官方库，常用插件，技术网站，技术公众号等

## <a name="index">Index </a> 
   * <a href="#0">1. 网络库</a>  
   * <a href="#1">2. 图片加载库</a>  
   * <a href="#2">3. 数据库</a>  
   * <a href="#3">4. key-value数据存储框架</a>  
   * <a href="#4">5. 权限库</a>  
   * <a href="#5">6. 数据解析</a>  
      * <a href="#6">6.1. Json数据解析</a>  
      * <a href="#7">6.2. Html数据解析</a>  
      * <a href="#8">6.3. Xml数据解析</a>  
   * <a href="#9">7. 响应式编程框架</a>  
   * <a href="#10">8. 组件/模块路由，通信框架</a>  
   * <a href="#11">9. 注解</a>  
   * <a href="#12">10. 文件上传/下载</a>  
      * <a href="#13">10.1. 上传</a>  
      * <a href="#14">10.2. 下载</a>  
   * <a href="#15">11. 视频播放器</a>  
   * <a href="#16">12. 音乐播放器</a>  
   * <a href="#17">13. 扫码库</a>  
   * <a href="#18">14. 工具类</a>  
   * <a href="#19">15. 日志类</a>  
   * <a href="#20">16. 性能检测</a>  
   * <a href="#21">17. 插件化框架</a>  
   * <a href="#22">18. 热修复框架</a>  
   * <a href="#23">19. UI框架</a>  
      * <a href="#24">19.1. Matrial Design</a>  
      * <a href="#25">19.2. 图片</a>  
         * <a href="#26">19.2.1. 图片裁剪</a>  
         * <a href="#27">19.2.2. 显示GIF图片的控件</a>  
         * <a href="#28">19.2.3. 图片压缩</a>  
         * <a href="#29">19.2.4. 图片毛玻璃、模糊处理库</a>  
         * <a href="#30">19.2.5. 图片滤镜</a>  
         * <a href="#31">19.2.6. 图片展示控件</a>  
         * <a href="#32">19.2.7. 图片选择器</a>  
      * <a href="#33">19.3. 动画</a>  
      * <a href="#34">19.4. Layout</a>  
      * <a href="#35">19.5. List/Grid</a>  
      * <a href="#36">19.6. Other</a>  

## <a name="0">1. 网络库</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架            | 介绍      | 特点  | 优点  | 缺点  | 官网或相关地址 |
|:-------------------|:----------|:----------|:----------|:----------|:----------|
| OkHttp             | Square公司出品，一个高效，高性能的http请求库 。  | 1.使用连接池来复用连接以提供效率<br>2.支持SPDY,共享同一个Socket来处理同一个服务器所有的请求<br>3.支持http2.0、Websocket<br>4.支持同步、异步执行<br>5.封装线程池、数据转换、参数使用、错误处理等<br>6.无缝支持Gzip来减少数据流量<br>7.缓存响应数据来减少重复的网络请求<br>8.能从很多常用的连接问题中自动恢复<br>9.解决了代理服务器问题和SSL握手失败问题| 拥有Nio和Okio，所以性能更高，请求、处理速度更快（io:阻塞式 nio：非阻塞式）|   | https://github.com/square/okhttp <br> https://square.github.io/okhttp/       |
| Retrofit           | Square公司出品，适用于 Android 和 Java 的类型安全 HTTP 客户端。基于注解。底层分装了OkHttp。  |1.Resrful api设计风格<br>2.支持同步、异步<br>3.通过注解配置请求，包括请求方法、参数、请求头、返回值等<br>4.可以搭配多种Converter将获得数据解析&序列化<br>5.支持Gson（默认）、Jsckson、Protobuf等<br>6.提供Rxjava支持 | 代码简化，结构彻底，职责细分；易于和rxjava使用    |     | https://github.com/square/retrofit <br> https://square.github.io/retrofit/    |
| android-async-http | Google推出的一个基于 Apache 的 HttpClient 库的 Android 异步、基于回调的 Http 客户端。    |1.基于HttpClient<br>2.在UI线程外、异步进行http请求<br>3.在匿名回调中处理请求结果，callback使用了Andorid的Handler发送消息机制在创建它的线程中执行<br>4.自动智能请求重试机制<br>5.持久化cookie存储，保存cookit到应用程序的SharedPreferences|   |  | https://github.com/loopj/android-async-http <br> http://loopj.com/android-async-http/ |
| Volley             | Google推出的异步网络请求框架。特别适合数据量小，通信频繁的网络操作。  |1.基于HttpUrlConnection,封装了UIL图片加载框架，支持图片加载<br>2.网络请求的排序、优先级处理缓存<br>3.多级别取消请求<br>4.Activity和生命周期的联动（Activity结束生命周期同时取消所有网络请求）| 拓展性好，可支持httpClient、HTTPURLConnection、okhttp    | 只适合小数据传输  | https://github.com/google/volley   |


Android6.0以后Google官方Api移除HttpClient，继续使用HttpClient及基于其封装的网络库(例如android-async-http）会出异常, 需要在build.gradle里添加
```java
android {
    useLibrary ‘org.apache.http.legacy’
}
```


另外还有国内开发者开发的一些网络库（[xUtils](https://github.com/wyouflf/xUtils3), [NoHttp](https://github.com/wyouflf/xUtils3), [afinal](https://github.com/yangfuhai/afinal), [okhttp-OkGo](https://github.com/jeasonlzy/okhttp-OkGo)等)，不过大部分许久未更新，已经不维护了，不推荐使用。


**主流使用方式：** OkHttp + Retrofit


## <a name="1">2. 图片加载库</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架                        | 介绍       | 优点       | 缺点  |  官网或相关地址 |
|:-------------------------------|:----------|:----------|:----------|:----------|
| Glide                          | Google出品的图片加载框架，基于Picasso，和Picasso一样使用简洁    | 1. 功能强大并且使用简洁 <br> 2. Bitmap 格式是 RGB_565 格式, 内存消耗少 <br> 3. 存储是动态的，是根据屏幕控件大小，来缓存对应尺寸的图片到本地内存，节省存储空间、加载速度也变快 <br> 4. 支持Gif    |     | https://github.com/bumptech/glide    |
| Picasso                        | Square公司开源的一个Android平台上的图片加载框架，简单易用    | 功能强大并且使用简洁    | 1. 不支持Gif <br> 2. Bitmap 格式是ARGB_8888 格式，相对耗内存 <br> 3. 只会缓存原始尺寸的图片, 因此加载速度比glide慢  | https://github.com/square/picasso    |
| Fresco                         |  Facebook 出品的图片加载框架    | 1. 在Native层优化内存，避免OOM出现 <br> 2. 加载大图时，有的图Glide和Picasso加载不出来，Fresco可以    | 使用相对麻烦，导入包体积大   | https://github.com/facebook/fresco    |
| Android-Universal-Image-Loader | 比较老的图片加载库，长时间未更新。不建议使用。   |     |     | https://github.com/nostra13/Android-Universal-Image-Loader    |



## <a name="2">3. 数据库</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Room    | Google出品，Room 在 SQLite 上提供了一个抽象层，以便在充分利用 SQLite 的强大功能的同时，能够流畅地访问数据库    | ---    | ---   |https://developer.android.google.cn/training/data-storage/room    |
| GreenDao    | greenDAO 是一个轻量级、快速的 Android ORM，可以将对象映射到 SQLite 数据库。 greenDAO 针对 Android 进行了高度优化，可提供出色的性能并消耗最少的内存   | ---   | ---   |https://github.com/greenrobot/greenDAO    |
| LitePal    | 无需编写SQL语句即可完成大部分数据库操作。 LitePal的设置也非常简单，您可以在不到5分钟的时间内将其集成到您的项目中。    | ---   | ---  | https://github.com/guolindev/LitePal   |
| Realm    | Realm 是一个直接在手机、平板电脑或可穿戴设备中运行的移动数据库。   | --- | --- | https://github.com/realm/realm-java    |



## <a name="3">4. key-value数据存储框架</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| MMKV    | 腾讯微信出品。基于 mmap 内存映射的 key-value 组件，底层序列化/反序列化使用 protobuf 实现，性能高，稳定性强. 目前可在 Android、iOS/macOS、Win32 和 POSIX 上使用.    | --- | --- | https://github.com/Tencent/MMKV    |
| DataStore    | Google出品。Jetpack DataStore 是一种数据存储解决方案，允许您使用协议缓冲区存储键值对或类型化对象。使用 Kotlin 协程和 Flow 以异步、一致的事务方式存储数据。    | --- | --- | https://developer.android.google.cn/topic/libraries/architecture/datastore   |



## <a name="4">5. 权限库</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| PermissionsDispatcher    | PermissionsDispatcher 提供了一个简单的基于注解的 API 来处理运行时权限。该库减轻了编写一堆检查语句所带来的负担，无论是否已授予您许可，以保持您的代码清洁和安全。    | ---   | ---  | https://github.com/permissions-dispatcher/PermissionsDispatcher    |
| RxPermissions    | 该库允许将 RxJava 与新的 Android M 权限模型一起使用。    | --- | --- | https://github.com/tbruyelle/RxPermissions    |
| EasyPermissions    | Google出品，EasyPermissions 是一个包装库，用于在面向 Android M 或更高版本时简化基本系统权限逻辑。    | --- | ---  | https://github.com/googlesamples/easypermissions    |
| PermissionX    | PermissionX 是一个扩展 Android 库，它使 Android 运行时权限请求变得非常容易。 您可以将其用于基本权限请求场合或处理更复杂的条件，例如显示理由对话框或手动转到应用程序设置以获取许可。    | --- | ---  | https://github.com/guolindev/PermissionX    |



## <a name="5">6. 数据解析</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
### <a name="6">6.1. Json数据解析</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Gson    | Google出品，可用于将 Java 对象转换为 JSON 字符串。 它还可用于将 JSON 字符串转换为等效的 Java 对象。    | --- | --- | https://github.com/google/gson    |
| FastJson    | 阿里巴巴出品，可用于将 Java 对象转换为 JSON 字符串。 它还可用于将 JSON 字符串转换为等效的 Java 对象。   | ---  | --- | https://github.com/alibaba/fastjson    |

### <a name="7">6.2. Html数据解析</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Jsoup    | 一个以最好的DOM，CSS和jQuery解析html的库  | --- | --- | https://github.com/jhy/jsoup  |


### <a name="8">6.3. Xml数据解析</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Dom4j    | 灵活的 Java XML 框架  | --- | --- | https://github.com/dom4j/dom4j  |



## <a name="9">7. 响应式编程框架</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| RxJava    | 一个通过使用 Java VM 的可观察序列组合编写异步和基于事件的程序的库。   | --- | --- | https://github.com/ReactiveX/RxJava    |
| RxAndroid | Android上的响应式扩展，在RxJava基础上添加了Android线程调度  | ---  | --- | https://github.com/ReactiveX/RxAndroid    |
| RxLifecycle  | 使用 RxJava 的 Android 应用程序生命周期处理 API | ---  | --- | https://github.com/trello/RxLifecycle  |
| RxBinding  | 提供用RxJava绑定Android UI的API | ---  | --- | https://github.com/JakeWharton/RxBinding |


## <a name="10">8. 组件/模块路由，通信框架</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| EventBus    | Android 和 Java 的事件总线(发布/订阅)，简化了Activities、Fragments、Threads、Services等之间的通信。更少的代码，更好的质量。 | ---  | ---  | https://github.com/greenrobot/EventBus    |
| Arouter    | 帮助 Android App 进行组件化改造的路由框架    | ---  | ---  | https://github.com/alibaba/ARouter    |



## <a name="11">9. 注解</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Hilt    | Google出品。 Hilt 是 Android 的依赖项注入库，可减少在项目中执行手动依赖项注入的样板代码。基于Dagger2。    | --- | --- | https://developer.android.google.cn/training/dependency-injection/hilt-android?hl=zh_cn    |
| Dagger2   | Google出品。 适用于 Android 和 Java 的快速依赖注入器。    | ---  | --- | https://github.com/google/dagger <br> https://developer.android.google.cn/training/dependency-injection/dagger-basics?hl=zh_cn    |
| Butter Knife    | Android大神JakeWharton之作。将 Android 视图和回调绑定到字段和方法。    | --- | --- | https://github.com/JakeWharton/butterknife    |
| AndroidAnnotations    | 加速Android开发，且易于维护    | ---  | --- | https://github.com/androidannotations/androidannotations    |



## <a name="12">10. 文件上传/下载</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>

### <a name="13">10.1. 上传</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| FileDownloader   | 安卓多任务文件下载引擎。  | 多任务、多线程（多连接）、断点续传、高并发、简单易用、单进程/非单进程     | 不支持文件上传。    | https://github.com/lingochamp/FileDownloader    |

### <a name="14">10.2. 下载</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>


## <a name="15">11. 视频播放器</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| JiaoZiVideoPlayer    | 媒体播放器（支持exoplayer，ijkplayer，ffmpeg）    | --- | --- | https://github.com/lipangit/JiaoZiVideoPlayer   |
| GSYVideoPlayer    | 基于IJKPlayer（兼容系统MediaPlayer与EXOPlayer2），实现了多功能的视频播放器。    | --- | ---  | https://github.com/CarGuo/GSYVideoPlayer    |
| ijkplayer    | Bilibili开源。基于FFmpeg n3.4的Android/iOS视频播放器，支持MediaCodec、VideoToolbox。    | ---  | ---  | https://github.com/bilibili/ijkplayer    |
| jjdxm_ijkplayer   | 基于ijkplayer简单的UI界面 当前项目是基于ijkplayer项目进行的播放器界面UI封装。 是一个适用于 Android 的 RTMP 播放界面 SDK，可高度定制化和二次开发。特色是同时支持 H.264 软编／硬编和 AAC 软编／硬编。主要是支持RIMP、HLS、MP4、M4A等视频格式的播放。    | --- | ---  | https://github.com/lingcimi/jjdxm_ijkplayer    |
| ExoPlayer    | Google开源的视频播放器   | ---  | ---  | https://github.com/google/ExoPlayer  |


## <a name="16">12. 音乐播放器</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| uamp  | google的跨平台音乐播放器，支持手机、平板、手表和TV，是学习多平台的最好实例 | ---  | ---  | https://github.com/android/uamp  |


## <a name="17">13. 扫码库</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| zxing    | 适用于 Java、Android 的条码扫描库。ZXing（“斑马线”）是一个开源的、多格式的一维/二维条码图像处理库，用 Java 实现，可移植到其他语言。    | ----    | ----    | https://github.com/zxing/zxing    |
| BGAQRCode-Android  | QRCode 扫描二维码、扫描条形码、相册获取图片后识别、生成带 Logo 二维码、支持微博微信 QQ 二维码扫描样式  | ----    | ----    | https://github.com/bingoogolapple/BGAQRCode-Android   |


## <a name="18">14. 工具类</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| AndroidUtilCode    | 一个功能强大且易于使用的 Android 工具库。 该库封装了Android开发中常用的功能。    | ----    | ----    | https://github.com/Blankj/AndroidUtilCode    |
| ToastCompat | 一个用于修复Toast在Android7.1上大概率出现android.view.WindowManager$BadTokenException问题的库。 | ---- |----|https://github.com/PureWriter/ToastCompat



## <a name="19">15. 日志类</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Logger  | Simple, pretty and powerful logger for android。    | ----    | ----    | https://github.com/orhanobut/logger   |
| Timber  | A logger with a small, extensible API which provides utility on top of Android's normal Log class.    | ----    | ----    | https://github.com/JakeWharton/timber   |


## <a name="20">16. 性能检测</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| LeakCanary    | Android 的内存泄漏检测库。 | ---    | ---  | https://github.com/square/leakcanary    |
| DoraemonKit | DoKit诞生于滴滴城运服体验技术部。一款面向泛前端产品研发全生命周期的效率平台。功能较多，其中包括性能检测。目前可在Android，ios, 小程序，Flutter, Web上使用。 | --- | ---  | https://github.com/didi/DoraemonKit    |
| matrix   | Matrix是微信中用来监控、定位和分析性能问题的APM（Application Performance Manage）。 它是一种插件风格的非侵入式解决方案，目前可在 iOS、macOS 和 Android 上使用    | ---   | --- | https://github.com/Tencent/matrix    |
| Android Profiler   | AndroidStudio自带的性能检测工具（包括Memory, CPU, NetWork, Energy(能耗，分析耗电量）    | ---    | ---   | https://developer.android.google.cn/studio/profile/android-profiler   |


## <a name="21">17. 插件化框架</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| RePlugin    | 360出品。一个灵活、稳定、易用的Android插件框架 | ---    | ---  | https://github.com/Qihoo360/RePlugin    |
| atlas | 阿里巴巴出品。Atlas是伴随着手机淘宝的不断发展而衍生出来的一个运行于Android系统上的一个容器化框架，我们也叫动态组件化(Dynamic Bundle)框架。它主要提供了解耦化、组件化、动态性的支持。 | --- | ---  | https://github.com/alibaba/atlas   |
| dynamic-load-apk   | android中的动态加载框架  | ---   | --- | https://github.com/singwhatiwanna/dynamic-load-apk   |
| Small | 做最轻巧的跨平台插件化框架。 | ---    | ---   | https://github.com/wequick/Small  |


## <a name="22">18. 热修复框架</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| tinker   | Tinker 是一款安卓热修复解决方案库，支持dex、库和资源更新，无需重新安装apk。 | ---    | ---  | https://github.com/Tencent/tinker  |


## <a name="23">19. UI框架</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>

### <a name="24">19.1. Matrial Design</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
1. [MetrialDesign官网](https://material.io/components?platform=android)
2. [material-components-android](https://github.com/material-components/material-components-android)

   Material Components for Android (MDC-Android) 帮助开发人员执行 Material Design。 这些组件由 Google 的工程师和 UX 设计师核心团队开发，可实现可靠的开发工作流程，以构建美观且功能强大的 Android 应用程序。


**建议：** 在实现UI效果时，优先考虑Material Design, 先从Material Desgin库里找相关的UI组件。如果没有需要的UI效果，再考虑找第三方库或者自己实现。

### <a name="25">19.2. 图片</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>

#### <a name="26">19.2.1. 图片裁剪</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| uCrop    | 提供终极且灵活的图像裁剪体验。 | ---   | --- |https://github.com/Yalantis/uCrop |


#### <a name="27">19.2.2. 显示GIF图片的控件</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| android-gif-drawable | 用于在 Android 上显示动画 GIF 的 Views 和 Drawable | ---   | --- | https://github.com/koral--/android-gif-drawable|

另外，图片加载框架里提到的Glide，Fresco也支持展示GIF图片。


#### <a name="28">19.2.3. 图片压缩</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Luban | Luban（鲁班） —— Android图片压缩工具，仿微信朋友圈压缩策略。可能是最接近微信朋友圈的图片压缩算法 | ---   | --- | https://github.com/Curzibn/Luban |
| Compressor | Compressor 是一个轻量级且功能强大的安卓图像压缩库。 | ---   | --- | https://github.com/zetbaitsu/Compressor |


#### <a name="29">19.2.4. 图片毛玻璃、模糊处理库</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| glide-transformations | 一个 Android 转换库，为 Glide 提供各种图像转换。支持模糊处理。 | --- | ---  | https://github.com/wasabeef/glide-transformations   |
| android-stackblur   | 可以根据渐变或半径对 Bitmap 执行模糊效果，并返回结果。 | ---    | ---  | https://github.com/kikoso/android-stackblur  |
| Blurry | 一个简单的 Android 模糊库 | --- | ---  | https://github.com/wasabeef/Blurry   |
| blurkit-android  | 一个非常易于使用和高性能的实用工具，用于在 Android 中渲染实时模糊效果。与 iOS 相似的快速模糊布局。 | ---   | --- | https://github.com/CameraKit/blurkit-android  |


#### <a name="30">19.2.5. 图片滤镜</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| glide-transformations | 一个 Android 转换库，为 Glide 提供各种图像转换。 | --- | ---  | https://github.com/wasabeef/glide-transformations   |
| android-gpuimage   | 基于 OpenGL 的 Android 过滤器（来自 GPUImage for iOS 的想法） | ---    | ---  | https://github.com/cats-oss/android-gpuimage |


#### <a name="31">19.2.6. 图片展示控件</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| PhotoView | 通过各种触摸手势支持缩放的 Android 图片预览。 | --- | ---  | https://github.com/Baseflow/PhotoView   |
| ShapeableImageView  | Google material库提供。支持圆角、圆形，描边等多种图像转换 | ---  | ---  |https://mp.weixin.qq.com/s/z3FkJHTSkH_TFis_VOdkSw <br> https://developer.android.google.cn/reference/com/google/android/material/imageview/ShapeableImageView?hl=en |
| ImageFilterView  | 可以用来做圆角图片，也可以叠加图片资源进行混合过滤. | ---    | ---  | https://mp.weixin.qq.com/s/V-jH0rlIUxgkjSbTV2WjrA <br> https://developer.android.google.cn/reference/kotlin/androidx/constraintlayout/utils/widget/ImageFilterView?hl=en |
| CircleImageView  | 适用于 Android 的圆形 ImageView。 | ---    | ---  | https://github.com/hdodenhof/CircleImageView  |
| RoundedImageView | 支持圆角、椭圆和圆形的ImageView。 | --- | ---  | https://github.com/vinc3m1/RoundedImageView  |


#### <a name="32">19.2.7. 图片选择器</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Matisse    | 一个精心设计的安卓本地图片和视频选择器 | ---   | --- | https://github.com/zhihu/Matisse  |
| ImagePicker  | 完全仿微信的图片选择，并且提供了多种图片加载接口，选择图片后可以旋转，可以裁剪成矩形或圆形，可以配置各种其他的参数 | --- | --- | https://github.com/jeasonlzy/ImagePicker   |
| boxing | 一个多媒体选择器库，B站出品。可以选择一张或者多张图片，提供预览和裁剪功能。同样支持gif图，选择视频和图像压缩功能 | --- | ---  | https://github.com/bilibili/boxing  |
| PhotoPicker | 仿微信的图片选择器 | --- | ---  | https://github.com/donglua/PhotoPicker   |

### <a name="33">19.3. 动画</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| lottie-android  | 解析使用 Bodymovin 导出为 json 的 Adobe After Effects 动画，并在移动设备上本地呈现它们！ | ---   | --- | https://github.com/airbnb/lottie-android  |
| AndroidViewAnimations | 强大的滑动布局！可以轻松集成到任何地方，ListView、GridView、ViewGroup 等。 | --- | ---  | https://github.com/daimajia/AndroidViewAnimations   |
| recyclerview-animators  | 一个 Android 动画库，可以轻松地将 itemanimator 添加到 RecyclerView 项目。 | ---   | --- | https://github.com/wasabeef/recyclerview-animators |


### <a name="34">19.4. Layout</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| WaveView | android 的波浪视图 | ---   | --- | https://github.com/john990/WaveView <br> https://github.com/gelitenight/WaveView |
| AndroidSwipeLayout | Cute view animation collection. | --- | ---  | https://github.com/daimajia/AndroidSwipeLayout |
| SwipeBackLayout | 一个 Android 库，可帮助您使用向后滑动手势构建应用程序。 | ---   | --- | https://github.com/ikew0ng/SwipeBackLayout |
| AndroidSlidingUpPanel | 该库提供了一种向您的 Android 应用程序添加可拖动的向上滑动面板（由 Google Music 和 Google Maps 流行）的简单方法。 | ---   | --- | https://github.com/umano/AndroidSlidingUpPanel |
| SmartRefreshLayout | 🔥下拉刷新、上拉加载、二级刷新、淘宝二楼、RefreshLayout、OverScroll，Android智能下拉刷新框架，支持越界回弹、越界拖动，具有极强的扩展性，集成了几十种炫酷的Header和 Footer。 | ---   | --- | https://github.com/scwang90/SmartRefreshLayout |
| FlexboxLayout | 将 CSS 弹性框布局模块的类似功能引入 Android。  | ---   | --- | https://github.com/google/flexbox-layout |
| hover | 悬浮按钮  | ---   | --- | https://https://github.com/google/hover |
| TapTargetView | Material design功能引导视图  | ---   | --- | https://github.com/KeepSafe/TapTargetView |


### <a name="35">19.5. List/Grid</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| BaseRecyclerViewAdapterHelper | 强大而灵活的RecyclerView Adapter, 可以实现多种复杂布局 | ---   | --- | https://github.com/CymChad/BaseRecyclerViewAdapterHelper |


### <a name="36">19.6. Other</a><a style="float:right;text-decoration:none;" href="#index"> [Top]</a>
1. [awesome-android-ui](https://github.com/wasabeef/awesome-android-ui)
 
    一个很棒的 Android UI/UX 库的精选列表。汇集了很多精美的第三方UI库，每个库都带有动图预览效果。
