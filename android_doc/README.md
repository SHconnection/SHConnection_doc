# Android 

Android 端和后端交互的脑图 还有 一些 原型图等等


# 一些信息：
teacher.xlxs 
student.xlxs
是两个表 

创建成功的班主任信息：
- 工号：201
- 密码：201
- 姓名：null(存储的数值为null)

二维码信息：![二维码](https://github.com/SHconnection/SHConnection_doc/blob/master/android_doc/classid_qrcode.jpg)

class_id = 28<br>
已经注册的家长信息：

- 姓名：唐相儒 
<br>学号：204（这个家长暂时没有加入这个班级）
<br>密码：205

- 姓名：普京
<br>学号：205
<br>密码：205

# 当前进度情况


## 登录模块    
- 基本封装                  完成
- 导入学生信息/老师信息       完成（使用了apache poi 包地size可能比较大）
- 二维码扫描/生成            完成（扫描自己生成地二维码未测试）
- 分角色登录/注册            完成
- 班主任注册                未完成

## 发送新的通知
- 发送新的通知               完成（未和后端交互）
- 图库选取                  完成
- 上传到七牛图床              完成
- 将信息上传到我方后端         完成


## 个人中心

（需要重构）


## 评价收集

（未完成）

