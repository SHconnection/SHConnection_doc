# 文字版脑图：

## 流程

```       
                            
                            
                                  1.我是班主任 -> 直接创建班级 -> 填写相关信息 （1）-> 生成二维码 
                                  -> 班主任的班级创建成功 返回班主任加入的班级的id 和 当前的班级的 id
 
                     1.我是老师 ->         
 
                                  2.我是普通老师 -> 填写老师所教的相关的科目 和 老师的工号 -> 验证成功返回老师所加入的班级 和 当前班级的 id
引导（Navigation）-> 
                                 
                                 1. 直接登录 -> 填写信息（孩子的学号）(2) -> 如果在数据库中有这个孩子 -> ok

                    2.我是家长 -> 

                                 2. 扫描二维码 -> 填写孩子的相关信息（主要是学号 做一个校验） -> "信息上传成功之后" 完成登录过程

````
## 注释

更多解释：
1. 家长和孩子是多对多的关系
家长通过切换孩子的学好来切换班级
2. 老师和班级是多对多的关系
在老师登录成功的时候会返回老师加入的班级的list

> (1)班主任在填写相关信息具体需要的信息：

(前端post的信息)
- 创建时间（自动生成）
- 班主任工号
- 班主任名称
- 科任老师的list
- 孩子的信息列表
- 班级名称 

其中科任老师和孩子的名称的list通过excel表格读取

后端将会返回一个班级的key 这样就会存储在二维码中 并且不会暴露给客户端

> (2)家长需要填写的信息
孩子的学号

如果孩子没有加入的班级的话会返回一个错误code，孩子加入的班级的过程是通过扫描二维码实现的

> (3) 成员管理
老师和家长可以在个人中心选择加入新的班级和退出班级

##  一些草图：
![登录和注册](https://static.dingtalk.com/media/lADPDgQ9qR0CyZfNA2DNBIA_1152_864.jpg_620x10000q90g.jpg?auth_bizType=IM&auth_bizEntity=%7B%22cid%22%3A%22185863030%3A267532292%22%2C%22msgId%22%3A%22516944196900%22%7D&open_id=185863030)

![个人中心管理](https://static.dingtalk.com/media/lADPDgQ9qR0CgArNBIDNA2A_864_1152.jpg_620x10000q90g.jpg?auth_bizType=IM&auth_bizEntity=%7B%22cid%22%3A%22185863030%3A267532292%22%2C%22msgId%22%3A%22516912456734%22%7D&open_id=185863030)
