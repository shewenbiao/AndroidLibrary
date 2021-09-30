# AndroidLibrary
Android主流的一些第三方库，Android官方库，常用插件，技术网站，技术公众号等

## 网络库
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


## 图片加载库
| 主流框架                        | 介绍       | 优点       | 缺点  |  官网或相关地址 |
|:-------------------------------|:----------|:----------|:----------|:----------|
| Glide                          | Google出品的图片加载框架，基于Picasso，和Picasso一样使用简洁    | 1. 功能强大并且使用简洁 <br> 2. Bitmap 格式是 RGB_565 格式, 内存消耗少 <br> 3. 存储是动态的，是根据屏幕控件大小，来缓存对应尺寸的图片到本地内存，节省存储空间、加载速度也变快 <br> 4. 支持Gif    |     | https://github.com/bumptech/glide    |
| Picasso                        | Square公司开源的一个Android平台上的图片加载框架，简单易用    | 功能强大并且使用简洁    | 1. 不支持Gif <br> 2. Bitmap 格式是ARGB_8888 格式，相对耗内存 <br> 3. 只会缓存原始尺寸的图片, 因此加载速度比glide慢  | https://github.com/square/picasso    |
| Fresco                         |  Facebook 出品的图片加载框架    | 1. 在Native层优化内存，避免OOM出现 <br> 2. 加载大图时，有的图Glide和Picasso加载不出来，Fresco可以    | 使用相对麻烦，导入包体积大   | https://github.com/facebook/fresco    |
| Android-Universal-Image-Loader | 比较老的图片加载库，长时间未更新。不建议使用。   |     |     | https://github.com/nostra13/Android-Universal-Image-Loader    |



## 数据库
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Room    | Google出品，Room 在 SQLite 上提供了一个抽象层，以便在充分利用 SQLite 的强大功能的同时，能够流畅地访问数据库    | ---    | ---   |https://developer.android.google.cn/training/data-storage/room    |
| GreenDao    | greenDAO 是一个轻量级、快速的 Android ORM，可以将对象映射到 SQLite 数据库。 greenDAO 针对 Android 进行了高度优化，可提供出色的性能并消耗最少的内存   | ---   | ---   |https://github.com/greenrobot/greenDAO    |
| LitePal    | 无需编写SQL语句即可完成大部分数据库操作。 LitePal的设置也非常简单，您可以在不到5分钟的时间内将其集成到您的项目中。    | ---   | ---  | https://github.com/guolindev/LitePal   |
| Realm    | Realm 是一个直接在手机、平板电脑或可穿戴设备中运行的移动数据库。   | --- | --- | https://github.com/realm/realm-java    |



## key-value数据存储框架
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| MMKV    | 腾讯微信出品。基于 mmap 内存映射的 key-value 组件，底层序列化/反序列化使用 protobuf 实现，性能高，稳定性强. 目前可在 Android、iOS/macOS、Win32 和 POSIX 上使用.    | --- | --- | https://github.com/Tencent/MMKV    |
| DataStore    | Google出品。Jetpack DataStore 是一种数据存储解决方案，允许您使用协议缓冲区存储键值对或类型化对象。使用 Kotlin 协程和 Flow 以异步、一致的事务方式存储数据。    | --- | --- | https://developer.android.google.cn/topic/libraries/architecture/datastore   |



## 权限库
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| PermissionsDispatcher    | PermissionsDispatcher 提供了一个简单的基于注解的 API 来处理运行时权限。该库减轻了编写一堆检查语句所带来的负担，无论是否已授予您许可，以保持您的代码清洁和安全。    | ---   | ---  | https://github.com/permissions-dispatcher/PermissionsDispatcher    |
| RxPermissions    | 该库允许将 RxJava 与新的 Android M 权限模型一起使用。    | --- | --- | https://github.com/tbruyelle/RxPermissions    |
| EasyPermissions    | Google出品，EasyPermissions 是一个包装库，用于在面向 Android M 或更高版本时简化基本系统权限逻辑。    | --- | ---  | https://github.com/googlesamples/easypermissions    |
| PermissionX    | PermissionX 是一个扩展 Android 库，它使 Android 运行时权限请求变得非常容易。 您可以将其用于基本权限请求场合或处理更复杂的条件，例如显示理由对话框或手动转到应用程序设置以获取许可。    | --- | ---  | https://github.com/guolindev/PermissionX    |



## JSON解析
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Gson    | Google出品，可用于将 Java 对象转换为 JSON 字符串。 它还可用于将 JSON 字符串转换为等效的 Java 对象。    | --- | --- | https://github.com/google/gson    |
| FastJson    | 阿里巴巴出品，可用于将 Java 对象转换为 JSON 字符串。 它还可用于将 JSON 字符串转换为等效的 Java 对象。   | ---  | --- | https://github.com/alibaba/fastjson    |



## 异步链式框架
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| RxJava    | 一个通过使用 Java VM 的可观察序列组合编写异步和基于事件的程序的库。   | --- | --- | https://github.com/ReactiveX/RxJava    |
| RxAndroid    | 配合Rxjava使用    | ---  | --- | https://github.com/ReactiveX/RxAndroid    |



## 组件/模块路由，通信框架
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| EventBus    | Android 和 Java 的事件总线(发布/订阅)，简化了Activities、Fragments、Threads、Services等之间的通信。更少的代码，更好的质量。 | ---  | ---  | https://github.com/greenrobot/EventBus    |
| Arouter    | 帮助 Android App 进行组件化改造的路由框架    | ---  | ---  | https://github.com/alibaba/ARouter    |



## 注解
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Hilt    | Google出品。 Hilt 是 Android 的依赖项注入库，可减少在项目中执行手动依赖项注入的样板代码。基于Dagger2。    | --- | --- | https://developer.android.google.cn/training/dependency-injection/hilt-android?hl=zh_cn    |
| Dagger2   | Google出品。 适用于 Android 和 Java 的快速依赖注入器。    | ---  | --- | https://github.com/google/dagger <br> https://developer.android.google.cn/training/dependency-injection/dagger-basics?hl=zh_cn    |
| Butter Knife    | Android大神JakeWharton之作。将 Android 视图和回调绑定到字段和方法。    | --- | --- | https://github.com/JakeWharton/butterknife    |
| AndroidAnnotations    | 加速Android开发，且易于维护    | ---  | --- | https://github.com/androidannotations/androidannotations    |



## 文件上传/下载
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| FileDownloader   | 安卓多任务文件下载引擎。  | 多任务、多线程（多连接）、断点续传、高并发、简单易用、单进程/非单进程     | 不支持文件上传。    | https://github.com/lingochamp/FileDownloader    |



## 视频播放器
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| JiaoZiVideoPlayer    | 媒体播放器（支持exoplayer，ijkplayer，ffmpeg）    | --- | --- | https://github.com/lipangit/JiaoZiVideoPlayer   |
| GSYVideoPlayer    | 基于IJKPlayer（兼容系统MediaPlayer与EXOPlayer2），实现了多功能的视频播放器。    | --- | ---  | https://github.com/CarGuo/GSYVideoPlayer    |
| ijkplayer    | 基于FFmpeg n3.4的Android/iOS视频播放器，支持MediaCodec、VideoToolbox。    | ---  | ---  | https://github.com/bilibili/ijkplayer    |
| jjdxm_ijkplayer   | 基于ijkplayer简单的UI界面 当前项目是基于ijkplayer项目进行的播放器界面UI封装。 是一个适用于 Android 的 RTMP 播放界面 SDK，可高度定制化和二次开发。特色是同时支持 H.264 软编／硬编和 AAC 软编／硬编。主要是支持RIMP、HLS、MP4、M4A等视频格式的播放。    | --- | ---  | https://github.com/lingcimi/jjdxm_ijkplayer    |


## 扫码库
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| zxing    | 适用于 Java、Android 的条码扫描库。ZXing（“斑马线”）是一个开源的、多格式的一维/二维条码图像处理库，用 Java 实现，可移植到其他语言。    | ----    | ----    | https://github.com/zxing/zxing    |


## 工具类
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| AndroidUtilCode    | 一个功能强大且易于使用的 Android 工具库。 该库封装了Android开发中常用的功能。    | ----    | ----    | https://github.com/Blankj/AndroidUtilCode    |
| ToastCompat | 一个用于修复Toast在Android7.1上大概率出现android.view.WindowManager$BadTokenException问题的库。 | ---- |----|https://github.com/PureWriter/ToastCompat



## 日志类
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Logger    | Simple, pretty and powerful logger for android。    | ----    | ----    | https://github.com/orhanobut/logger   |



## 性能检测
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| LeakCanary    | Android 的内存泄漏检测库。 | ---    | ---  | https://github.com/square/leakcanary    |
| DoraemonKit | DoKit诞生于滴滴城运服体验技术部。一款面向泛前端产品研发全生命周期的效率平台。功能较多，其中包括性能检测。目前可在Android，ios, 小程序，Flutter, Web上使用。 | --- | ---  | https://github.com/didi/DoraemonKit    |
| matrix   | Matrix是微信中用来监控、定位和分析性能问题的APM（Application Performance Manage）。 它是一种插件风格的非侵入式解决方案，目前可在 iOS、macOS 和 Android 上使用    | ---   | --- | https://github.com/Tencent/matrix    |
| Android Profiler   | AndroidStudio自带的性能检测工具（包括Memory, CPU, NetWork, Energy(能耗，分析耗电量）    | ---    | ---   | https://developer.android.google.cn/studio/profile/android-profiler   |


## 插件化框架
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| RePlugin    | 360出品。一个灵活、稳定、易用的Android插件框架 | ---    | ---  | https://github.com/Qihoo360/RePlugin    |
| atlas | 阿里巴巴出品。Atlas是伴随着手机淘宝的不断发展而衍生出来的一个运行于Android系统上的一个容器化框架，我们也叫动态组件化(Dynamic Bundle)框架。它主要提供了解耦化、组件化、动态性的支持。 | --- | ---  | https://github.com/alibaba/atlas   |
| dynamic-load-apk   | android中的动态加载框架  | ---   | --- | https://github.com/singwhatiwanna/dynamic-load-apk   |
| Small | 做最轻巧的跨平台插件化框架。 | ---    | ---   | https://github.com/wequick/Small  |


## 热修复框架
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| tinker   | Tinker 是一款安卓热修复解决方案库，支持dex、库和资源更新，无需重新安装apk。 | ---    | ---  | https://github.com/Tencent/tinker  |


## UI框架
### 图片

#### 图片裁剪
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| uCrop    | 提供终极且灵活的图像裁剪体验。 | ---   | --- |https://github.com/Yalantis/uCrop |


#### 显示GIF图片的控件
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| android-gif-drawable | 用于在 Android 上显示动画 GIF 的 Views 和 Drawable | ---   | --- | https://github.com/koral--/android-gif-drawable|

另外，图片加载框架里提到的Glide，Fresco也支持展示GIF图片。


#### 图片压缩
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Luban | Luban（鲁班） —— Android图片压缩工具，仿微信朋友圈压缩策略。可能是最接近微信朋友圈的图片压缩算法 | ---   | --- | https://github.com/Curzibn/Luban |


#### 图片毛玻璃、模糊处理库
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| glide-transformations | 一个 Android 转换库，为 Glide 提供各种图像转换。支持模糊处理。 | --- | ---  | https://github.com/wasabeef/glide-transformations   |
| android-stackblur   | 可以根据渐变或半径对 Bitmap 执行模糊效果，并返回结果。 | ---    | ---  | https://github.com/kikoso/android-stackblur  |
| Blurry | 一个简单的 Android 模糊库 | --- | ---  | https://github.com/wasabeef/Blurry   |
| blurkit-android  | 一个非常易于使用和高性能的实用工具，用于在 Android 中渲染实时模糊效果。与 iOS 相似的快速模糊布局。 | ---   | --- | https://github.com/CameraKit/blurkit-android  |


#### 图片滤镜
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| glide-transformations | 一个 Android 转换库，为 Glide 提供各种图像转换。 | --- | ---  | https://github.com/wasabeef/glide-transformations   |
| android-gpuimage   | 基于 OpenGL 的 Android 过滤器（来自 GPUImage for iOS 的想法） | ---    | ---  | https://github.com/cats-oss/android-gpuimage |


#### 图片展示控件
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| PhotoView | 通过各种触摸手势支持缩放的 Android 图片预览。 | --- | ---  | https://github.com/Baseflow/PhotoView   |
| ShapeableImageView  | Google material库提供。支持圆角、圆形，描边等多种图像转换 | ---  | ---  |https://mp.weixin.qq.com/s/z3FkJHTSkH_TFis_VOdkSw <br> https://developer.android.google.cn/reference/com/google/android/material/imageview/ShapeableImageView?hl=en |
| ImageFilterView  | 可以用来做圆角图片，也可以叠加图片资源进行混合过滤. | ---    | ---  | https://mp.weixin.qq.com/s/V-jH0rlIUxgkjSbTV2WjrA <br> https://developer.android.google.cn/reference/kotlin/androidx/constraintlayout/utils/widget/ImageFilterView?hl=en |
| CircleImageView  | 适用于 Android 的圆形 ImageView。 | ---    | ---  | https://github.com/hdodenhof/CircleImageView  |
| RoundedImageView | 支持圆角、椭圆和圆形的ImageView。 | --- | ---  | https://github.com/vinc3m1/RoundedImageView  |


#### 图片选择器
| 主流框架  | 介绍  | 优点  | 缺点  |  官网或相关地址      |
|:----------|:----------|:----------|:----------|:----------|
| Matisse    | 一个精心设计的安卓本地图片和视频选择器 | ---   | 长期未维护 | https://github.com/zhihu/Matisse  |
| PhotoPicker | 仿微信的图片选择器 | --- | 长期未维护  | https://github.com/donglua/PhotoPicker   |
| ImagePicker  | 完全仿微信的图片选择，并且提供了多种图片加载接口，选择图片后可以旋转，可以裁剪成矩形或圆形，可以配置各种其他的参数 | ---   | 已停止维护 | https://github.com/jeasonlzy/ImagePicker   |

