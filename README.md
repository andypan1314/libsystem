# Demo<div align="center">
	<a href="https://youtu.be/p6Gvnx3LSTs">    <img src="https://j.gifs.com/xGgmWn.gif" width = "360"  target="https://youtu.be/p6Gvnx3LSTs" /> </a>     
    <a href="https://www.youtube.com/watch?v=8rJvrR23OgY">    <img src="https://j.gifs.com/wj1lzg.gif" width = "360"  target="https://youtu.be/p6Gvnx3LSTs" /> </a> </div># 项目简介凌志图书管理系统将微信小程序（10%代码量）与网站平台(90%代码量)相结合，利用短信网关等服务旨在在为用户创建一个完善的图书信息服务平台。	网站平台分为管理员模块和用户模块，用户可以在平台中完成图书查询、借阅等一系列用户操作；管理员模块可以完成图书信息、借阅信息、用户信息的维护，权限管理，以及使用短信通知服务等。	微信平台面小程序向用户，主要是将豆瓣读书的海量数据与图书馆系统中书籍数据相结合，用户可以通过豆瓣提供的书籍信息、评分等信息选择感兴趣的书籍，瞬间完成在图书馆内相关书籍的借阅，免去重新登录再借阅的麻烦，使图书馆不单单是一个传统的管理软件，而是一个图书和读者之间沟通的纽带。	项目开发前后克服很多困难与挑战，前期认真学习了Bootstrap、JQuery、Ajax、Datatables等前端技术，PHP、Linux基本操作、Docker、Nginx、HTTP协议等服务器端基本常识，Git版本控制管理以及多线程、死锁、饥饿等操作系统和数据库中的并发控制相关知识，于4月17日完成本项目。# 访问方法## Web端访问方法 ### 方案一访问[demo](https://demo.silenx.me/libsystem)管理员测试帐号：10000 管理员密码：123456普通用户测试帐号：201437001 普通用户测试密码：123456测试环境：Linux VM_104_147_centos 3.10.0-327.36.3.el7.x86_64### 方案二1. git clone https://github.com/woooosz/libsystem2. 登录mysql使用source（或使用phpmyadmin等图形化界面），将目录文件夹下的libsystem.sql导入到数据库中（已经包含部分测试数据）3. 配置web目录下的conn.php,设置数据库信息。4. 访问http://localhost/libsystem 其中普通用户测试帐号：201437001 普通用户测试密码：123456；管理员测试帐号：10000 管理员密码：123456## 小程序访问方法1. 访问 https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html 下载小程序开发套件2. 导入项目dainidu-weapp之后通过模拟程序访问普通用户测试帐号：201437001 普通用户测试密码：123456# 系统架构设计## 网站架构设计以图书日常管理工作为主线，将涉及图书日常管理的图书上架图书查找、借阅、图书归还、图书借阅人管理、记录。以及其他日常管理（超期罚款）等方便图书管理员对图书进行管理，又方便读者借阅，提高图书管理、利用的效率。## 管理员模块1. 登录模块，主要实现登录账户密码的验证工作。 2. 基本信息设置保证图书信息和读者信息的分类管理。3. 图书信息、借阅信息查询功能，保证数据查询的灵活性。 4. 结合阿里大于提供的短信网关产生借阅信息提醒功能，使用户可以及时掌握借阅欠款信息。5. 提供管理员的信息维护功能，保证信息的安全性 。 6. 提供灵活、方便的权限设置功能。管理不同用户组的借阅天数等信息设置。## 用户功能模块1. 登录模块，完成帐号的验证工作。2. 图书信息检索，根据支持ISBN和图书名称两种模式查询本图书馆的信息，支持模糊匹配。3. 借阅信息查询，查看自己当前罚金等。4. 个人信息维护，修改密码，修改手机联系方式、邮箱等个人信息。## 小程序架构设计『凌志带你读』是凌志图书管理系统下的一个小功能，旨在充当『图书与读者』之间沟通的桥梁，帮助读者选择潜在感兴趣的书籍，微信小程序对接豆瓣图API，支持海量数据检索。支持一键借阅对应图书馆中对应的书籍，免去了读者重新登录网站平台检索借阅等操作。# 设计重点与难点## 前台技术难点1. 大数据量时手机页面的排版优化，最终能让数据一目了然。2. 不同用户在不同状态（浏览器、设备）下看到的界面存在差异，需要复杂的JS来控制3. 多设备的适配花费了大量的精力4. 前台设计涉及到了大量的报表综上所述，我选择了JQuery、bootstrap、Datatables三个框架以提高开发效率。## 服务端技术难点1. 凌志图书管理系统的设计重点在于数据库的设计，在概念数据模型时需要遵守第三范式，然而为了提高运行效率，需要人为降低数据冗余，因此在效率是一个挑战。此外，也设计到了大量的视图、触发器的设计，增加了数据库设计的复杂度。2. 由于数据交互量大，数据库操作频繁，本项目采用了数据库连接池来优化数据库的操作，选用了MySql来做未平台后台数据库管理系统。具有轻量级、跨平台、查询效率极高、使用事务完成速度快的特点。3. 凌志图书管理系统选择PHP来做为后台开发语言，PHP具有良好的安全性、跨平台特性、很好的移植性，且学习成本低，适合快速开发的要求。4. 小程序目前开发教程资料比较少，学习成本也是一个问题。5. 为了解决生产环境、开发环境的版本迭代，以及版本控制等问题，项目使用了Git，托管于Github。## 系统创新点系统的创新点在于**界面设计**和**功能创新**，界面主要采用**响应式设计**、**扁平化设计**。功能创新方面主要是将豆瓣读书的海量数据与图书馆系统中书籍数据相结合，用户可以通过豆瓣提供的书籍信息、评分等信息选择感兴趣的书籍，瞬间完成在图书馆内相关书籍的借阅，免去重新登录再借阅的麻烦，使图书馆不单单是一个传统的管理软件，而是一个图书和读者之间沟通的纽带；前台设计涉及到了近年来逐渐流行的**通知短信**，管理员可以进行短信群发等操作，无形中提高了管理效率。	# 系统不足之处* 从架构方面考虑，服务器端程序绝大多数代码还是面向过程方式设计，不符合当今主流的面向对象开发思想。各个模块如获取图书等API耦合度较高，应该统一封装、管理。* 从性能影响方面考虑，还有改善的空间，可以将Dash运行状态板上面的统计统计数据使用Redis或Memcache进行缓存处理，有效减轻数据库的负荷。* 从数据库性能优化中，很多服务器端中的SQL语句还有待优化，诸如避免使用『*』，用『>=』替代『>』等，这些小技巧在服务器端代码设计后才学到，因此没有机会在这个系统去应用。* 如果并发量再大一些，可以考虑引入PHP+Redis消息队列的机制，实现瞬时流量的削峰的效果。