# PyFly

#### 更新记录

2018.06.13 学校专业实训的第三天，实在太闲，进行了一下压测，吞吐量惨不忍睹，加上redis缓存，稍微好了一些

2018.06.11 实现简单的签到功能，奖励为1-100的随机值

2018.05.08 开发者审核迟迟未通过，没法玩微博账号登录，突然想起搜索还没做，看了一会whoosh文档就开了撸了一波代码，用了jieba分词，效果还行

#### 项目介绍
Flask + Layui Fly Template实现的一个社区项目，使用flask-admin实现了简单的后台管理功能，数据库使用Ｍongodb，前台实现功能：用户注册、登录、邮件激活、发帖、回帖、点赞、回复、采纳、删帖、结贴等功能

#### 软件架构
1.前端模板：[Layui Fly Template](http://www.layui.com/template/fly/)

2.Flask + flask-pymongo + flask-admin + flask-login + flask-mail



#### 安装教程

```
git clone https://gitee.com/981764793/PyFly

安装MongoDB
修改mongodb连接信息，STMP邮箱账号密码（用户注册验证用到）


pip install -r requirements.txt

python manager.py runserver
```

```aiignore
pip uninstall Werkzeug

pip install -U Werkzeug==0.16.0
```

```aiignore
helpers.py

from urlparse import quote as url_quote

from urllib.parse import quote as url_quote
```

```aiignore
Flask	0.12.2	3.1.0
Flask-Admin	1.6.1	1.6.1
Flask-Cache	0.13.1	0.13.1
Flask-Login	0.4.1	0.6.3
Flask-Mail	0.9.1	0.10.0
Flask-OAuthlib	0.9.4	0.9.6
Flask-PyMongo	0.5.1	3.0.1
Flask-Script	2.0.6	2.0.6
Flask-Uploads	0.2.1	0.2.1
Flask-WTF	0.14.2	1.2.2
Jinja2	2.10.3	3.1.5
MarkupSafe	1.1.1	3.0.2
WTForms	2.1	3.2.1
Werkzeug	0.16.1	3.1.3
Whoosh	2.7.4	2.7.4
blinker	1.4	1.9.0
certifi	2018.4.16	2025.1.31
chardet	3.0.4	5.2.0
charset-normalizer	3.4.1	3.4.1
click	6.7	8.1.8
colorama	0.4.6	0.4.6
dnspython	2.7.0	2.7.0
idna	2.7	3.10
idna	3.10	3.10
itsdangerous	1.1.0	2.2.0
jieba	0.39	0.42.1
oauthlib	2.1.0	3.2.2
pillow	11.1.0	11.1.0
pip	25.0.1	25.0.1
pymongo	3.9.0	4.11.1
pymongo	4.11.1	4.11.1
python-dateutil	2.7.5	2.9.0.post0
redis	3.0.1	5.2.1
requests	2.19.0	2.32.3
requests-oauthlib	1.1.0	2.0.0
setuptools	68.2.0	75.8.0
six	1.12.0	1.17.0
six	1.17.0	1.17.0
urllib3	2.3.0	2.3.0
urlparser	0.1.2	0.1.2
wheel	0.41.2	0.45.1
```

#### 使用说明

1. 首次打开会自动往MongoDB新增一些默认数据（管理员账号和默认配置项），后台管理（flask-admin简单实现）: http://127.0.0.1:5000/admin

2. 可自己修改扩展模板作为信息分类网站或者简单的cms、博客

3.图片上传可选保存到后端或图床，默认保存到服务器，如果要开启图床上传在/static/js/mods/index.js搜索开启图床注释和解开相应注释后即可，然后在user.js进行相应操作，图床使用了[SM.MS图床](http://sm.ms)

#### 模板开发

1.全局过滤器mongo_date_str（格式化mongodb的日期字段）

2.全局函数：

    1）get_page(collection_name, pn=1, size=10, sort_by=None, filter1=None) 分页查询 pn页码 sort_by为tuple类型，目前只支持单字段排序，详情可看模板
    2）get_list(collection_name, sort_by=None, filter1=None, size=None) 列表查询
    3）find_one(collection_name, filter1=None) 获取单条
    4）date_cal(d1, num, is_add=True) 计算日期


#### Todo

1.社交账号登录

2.暂时没想到。。。

#### 截图预览

![首页1](https://gitee.com/uploads/images/2018/0426/180217_6c36771c_750007.png "QQ截图20180426175656.png")

![首页2](https://gitee.com/uploads/images/2018/0426/180231_079d2ac1_750007.png "QQ截图20180426175715.png")

![发帖](https://gitee.com/uploads/images/2018/0426/180246_dd80896b_750007.png "QQ截图20180426175740.png")

![回帖](https://gitee.com/uploads/images/2018/0426/180259_11602e95_750007.png "QQ截图20180426175828.png")

![个人设置](https://gitee.com/uploads/images/2018/0426/180310_de7a3005_750007.png "QQ截图20180426175906.png")

![用户主页](https://gitee.com/uploads/images/2018/0426/180325_60301b7a_750007.png "QQ截图20180426175922.png")