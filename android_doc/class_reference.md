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


# ScanActivity
将扫描之后的结果放到回传到相关的Activity中
***
# ContextExtension
- 封装了一个Anko SqliteDataBase的实例
