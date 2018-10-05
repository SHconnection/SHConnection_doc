# NavigationAcivity.kt
- 完成各种permission的请求
- 导引和分发家长和老师用户到不同的登录页面中

# LoginActivity 
老师和家长登录使用同一个登录入口 

通过NavigationAcvity 传入一个参数 判断用户的类型 然后进行页面的update， 或者使用不同的api
不管是家长还是孩子在创建完成之后，都会返回一个token 这个token 暂时是不会变化的

- 在老师登录完成之后会在数据库中持久化一个老师的加入的班级的list
- 并且将当前老师所在的id 和 家长所在地id 保存在CLASS_ID	中
如果点击创建班级会导引到老师创建班级的页面中去。
- todo
 老师的api 未完成 
 家长的api 未完成

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


## todos
- 如何获取到存储在手机中的xlxs？
- 储存生成地二维码



# ScanActivity
将扫描之后的结果放到回传到相关的Activity中
***
# ContextExtension
- 封装了一个Anko SqliteDataBase的实例


## 注释
- 后端返回的数据中 CLASS_ID 客户端用来储存已经完成创建地班级id  CLASSED_IDS 表示老师加入地班级列表，是一个被持久化了的表名
CLASS_ID   储存在客户端地手机上地时候是没有加密的 只有在二维码中才可以加密