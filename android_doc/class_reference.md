# 导入了什么来加快开发进度：
- Anko sqlite
- Kotlin协程库
- Anko common库
- 已经配置了超级简单的图片加载库 picasso

***
# 基础封装篇：
- Retrofit + RxJava 网络请求 RetrofitService.kt 写网络请求的接口 Data.kt 放所有地实体类class
- ToolbarAcvitity 基本的 toolbar封装 使用的时候需要在xml include 一个view 可以参考以下ToolbarAcitivity继承类
- ContextExtentions.kt 这个类中有封装了很多Snackbar 和 toast 相关操作。toast 相关操作也可以使用Anko common中的dsl
可以通过getValue setValue设置SharedPreference的值 
（10.9合并kolibreath 分支）
~~``小心！``调用的时候推荐使用``App.getContext.getValue（）`` 这是由于Acitvity的初始化时间的问题~~
此问题已经修复，可以查看源码了解详情

*** 
# 类引用篇：

# NavigationAcivity.kt
- 完成各种permission的请求
- 导引和分发家长和老师用户到不同的登录页面中

# LoginActivity 
老师和家长登录使用同一个登录入口 

通过NavigationAcvity 传入一个参数 判断用户的类型 然后进行页面的update， 或者使用不同的api
不管是家长还是孩子在创建完成之后，都会返回一个token 这个token 暂时是不会变化的

- 在老师登录完成之后会在数据库中持久化一个老师的加入的班级的list
- 并且将当前老师所在的id 和 家长所在地id 保存在CLASS_ID	中
会在本地持久化 
班级id 
学号/教师工号 id  
Token 
用户类型 ：是老师还是学生
教师或者是学生名字

# MainActivity.java
使用Java 写成的，一个基础的放置Fragment的容器
 # ScanActivity(废弃)
 如果需要扫描功能地类都需要路由到这里
 扫描完成的intent 中会携带加密过了的班级的class_id

# JoinClassActivity
加入一个班级
在这个班级的老师需要输入相同地用户名和工号才可以加入
同样学生也需要输入相同地用户名和学号

# ViewPictureActivity
发送一条新的动态    
有两种类型的动态 一种是通知一种是消息
可以预览图片

# DatabaseHelper 
使用Kotlin Anko库完成的数据库操作 用于持久化一些数据结构
[Anko Sqlite](https://github.com/Kotlin/anko/wiki/Anko-SQLite#accessing-database)
可以之用写一个数据库helper然后创建多个表的实例
都是需要通过SqliteDatabse 来操纵

需要创建一个管理所有的表的表
所有的表的记录结果

# XlsUtils
解析数据格式：
- 学生数据格式：
张三 2016210
王五 201231

apache 解析xml的程序不太友好 因为Android 使用的jre中有部分类缺失，所以apk 的 size很成问题


## todos
- 如何获取到存储在手机中的xlxs？
- 储存生成地二维码



# ScanActivity
将扫描之后的结果放到回传到相关的Activity中
***
# ContextExtension
- 封装了一个Anko SqliteDataBase的实例 可以使用这个调用数据库


## 注释

> 用户完成登录之后干了什么：

登录的用户可能是老师也可能是家长，

- 通过保存当前用户登录的帐号（工号或则是学号的方法判断用户有没有登录成功）
- 通过USER_TYPE 这个Preference的key表示用户类型
- 后端返回的数据中 CLASS_ID 客户端用来储存已经完成创建地班级id  CLASSED_IDS 表示老师加入地班级列表，是一个被持久化了的表名
CLASS_ID   储存在客户端地手机上地时候是没有加密的 只有在二维码中才可以加密
- 并且持久化不会变化的Token 它的key是LOGIN_TOKEN    

- 如果是老师登录完成的话，会选取最后一个class_id作为当前地classid，家长登录完成也会有一个id 作为当前地class_id
之后通过这个class_id判断老师是否登录成功