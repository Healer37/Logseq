---
title: W--数据
---

## 分析思维
### 数据思维
#### 数学知识
##### 统计

##### 概率

### **业务思维** ~ 对一个行业的理解

## 工具使用
### 数据  **采集**
#### 埋点

#### 爬虫

#### 程序应用接口(API)

#### ---

#### 如何规划数据埋点
##### 数据埋点
###### 业务需求拆解, 转化为数据需求

###### 定义数据口径和指标统计方式
####### a. 各类事件的分类和聚合(事件类型, 页面位置)

####### b. 确定指标的数据类型 计数方式和记录规则

####### c. 4W1H(who what when where how)模型来选择数据

##### 数据埋点的分类
###### 点击事件(交互事件)

###### 曝光事件

###### 页面停留时间

### 数据  **整理与清洗**
#### numpy_python 库
##### [[🍃 知识]] ~ [Python数据分析与展示_中国大学MOOC(慕课)](https://www.icourse163.org/learn/BIT-1001870002?tid=1461061450#/learn/content?type=detail&id=1237317465&cid=1257276108&replay=true)

##### [NumPy v1.19手册](https://numpy.org/doc/stable/)

##### [NumPy | 菜鸟教程](https://www.runoob.com/numpy/numpy-tutorial.html)

#### pandas_python 库
##### [Pandas 中文](https://www.pypandas.cn/)

#### 数据库
##### 结构化 数据库

##### 非结构化 数据库

##### ---

##### MySQL
###### [MySQL 教程 | 菜鸟教程](https://www.runoob.com/mysql/mysql-tutorial.html)

###### [21分钟 MySQL 入门教程 - wid - 博客园](https://www.cnblogs.com/mr-wid/archive/2013/05/09/3068229.html)

###### [CodingLabs - MySQL索引背后的数据结构及算法原理](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)

###### [3000字！5大SQL数据清洗方法！](https://mp.weixin.qq.com/s?__biz=MzU5NDgyMjc0OQ==&mid=2247496131&idx=1&sn=36bdb62e19d35186979af8543f90bd8c&chksm=fe79e2f1c90e6be7629602d8df3f54deb05888c81c6485871a08ae826e826131b658938b814d&mpshare=1&scene=1&srcid=10254N4oJbu7VfYrLvHgir5j&sharer_sharetime=1603633517044&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.31.2998&platform=win&rd2werd=1#wechat_redirect)

##### **Excel**

##### ---

##### NoSQL

##### Hive

##### Oracle

##### Hadoop

##### MongoDB  ~ 非关系型数据库

#### ---

#### 保证数据的质量, 就是保证数据分析的质量
##### 高质量的数据应当符合以下标准:
###### 完整性

###### 唯一性

###### 准确性

###### 一致性

#### 整洁有序的数据, 可以提高数据分析的工作效率
##### eg:
###### 每个变量独占一列

###### 每条数据独占一行

### 数据  **分析与建模**
#### 🔨工具
##### [Project Jupyter | Home](https://jupyter.org/)

##### [Looker - 智能商业数据分析](https://looker.com/) ~ 谷歌
###### [Getting Started - How To Use Looker Tutorial | Looker](https://looker.com/guide/getting-started)

#### 统计学
##### [哈里斯堡社区大学公开课：统计学入门_全24集_网易公开课](https://link.zhihu.com/?target=http%3A//open.163.com/special/opencourse/statistics.html)

##### 均值，中位数，众数，标准差/方差，相关系数，协方差矩阵；

##### 概率分布（二项分布、泊松分布、正态分布），p值，贝叶斯定理（精度、召回率、阳性预测值、阴性预测值、混淆矩阵、ROC曲线）；

##### 中心极限定理，R2_score，MSE（均方误差），A / B测试，蒙特卡洛模拟…

#### 概率论

#### 多变量微积分
##### 多变量函数；

##### 导数和梯度；

##### 阶跃函数，Sigmoid函数，Logit函数，ReLU函数（整流线性单位函数，Rectified Linear Unit）；

##### 成本函数；

##### 函数绘图；

##### 函数的最小值和最大值…

#### 线性代数
##### 向量；

##### 向量的范数；

##### 矩阵，转置矩阵，矩阵的逆，矩阵的行列式，矩阵的迹；

##### 点积，特征值，特征向量…

#### 优化方法
##### 成本函数/目标函数；

##### 似然函数；

##### 损失函数；

##### 梯度下降算法及其变体（例如，随机梯度下降算法）…

#### 机器学习/深度学习

#### sklearn 库

#### 

#### [京东是如何用大数据洞察消费的？](https://daxuepc.com/detail/v_5f55985de4b0b5edf0a0973a/3)
##### ![](https://i.loli.net/2020/09/09/HoQGBKLcde5k6tw.png)

##### 用户画像

##### 小区画像

##### 商家画像

##### 商品画像

#### [耿直：统计学中的因果推断问题（Causal Inference）](https://mp.weixin.qq.com/s?__biz=MzI1MjQ2OTQ3Ng==&mid=2247512578&idx=2&sn=acf7ac0a15040bcf109da9d3cb2515a5&chksm=e9e1bb89de96329fb33dbc92ba7be53cd04c3b37046225625077b2595d31a64599758f4a045a&mpshare=1&scene=1&srcid=09117tBYN9Hz9d8BtxRCAq1B&sharer_sharetime=1599836626692&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.30.2006&platform=win&rd2werd=1#wechat_redirect)

### 数据  **可视化与制表**
#### python 可视化库
##### Matplotlib

##### Seaborn

##### Bokeh

##### Plotly

##### [pyecharts](https://pyecharts.org/#/?id=pyecharts) ~ 百度开源可视化库
###### [中文简介 - Document](https://gallery.pyecharts.org/#/README)

###### [链式调用](https://juejin.im/post/6844903720103182350)

##### Mapbox

##### Geoplotlib

#### [Tableau](https://www.tableau.com/zh-cn)

#### Power BI ~ 微软

#### Fine BI ~ 帆软

#### Quick BI ~ 阿里

#### MicroStrategy

#### 大屏可视化工具
##### DataV ~ 天猫双十一大屏

##### FineReport

#### [数据看板怎么搭？这里有 3 大原则和 4 大构成要素](https://mp.weixin.qq.com/s?__biz=MzI2MTAxOTk5OQ==&mid=2650948205&idx=1&sn=781ddf6b4aeff0b5c372778b6d67525a&chksm=f196225dc6e1ab4b01614a35db0ffa1963f4e76b50f3f70dbaf9b823123ee7279bbff39eaa2f&mpshare=1&scene=1&srcid=0909ttbeOL4Xv4vddYwUS47W&sharer_sharetime=1599695640786&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.30.2006&platform=win#rd)

#### [Python数据可视化工具怎么选？深度评测5款实用工具](https://mp.weixin.qq.com/s?__biz=MzI5OTk5OTM2Mw==&mid=2247516126&idx=2&sn=39dc197e34fa294fb7d299d1b6196d24&chksm=ec8cf632dbfb7f2423ad58da04f63b298980d86d184fad5d2c3cab065e5ffac032f5bd0b7293&mpshare=1&scene=1&srcid=0926HE2sr70rD3BjSoZlHX9L&sharer_sharetime=1601077910673&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.31.2998&platform=win#rd)

### 数据  **业务决策**

### ---

## 沟通表达
### 数据可视化

### 驱动项目落地

### 分析报告

## 组织协作
### 命名问题

### 数据标准

## 

## 课程
### [[🍃 知识]] ~ [[Course_京东数据分析]]

### [[🍃 知识]] ~ [C201022_数据分析45讲](https://time.geekbang.org/column/article/73248)
#### 

#### 算法
##### 分类算法：
###### C4.5

###### 朴素贝叶斯（Naive Bayes）

###### SVM

###### KNN

###### Adaboost

###### CARTl 

##### 聚类算法：
###### K-Means

###### EMl 

##### 关联分析：
###### Aprioril 

##### 连接分析：
###### PageRank

#### 数学原理
##### 概率论与数据分析

##### 线性代数

##### 图论

##### 最优化方法

#### 用户行为分析
##### 用户标签：
###### 它包括了性别、年龄、地域、收入、学历、职业等。这些包括了用户的基础属性。

##### 消费标签：
###### 消费习惯、购买意向、是否对促销敏感。这些统计分析用户的消费习惯。

##### 行为标签：
###### 时间段、频次、时长、访问路径。这些是通过分析用户行为，来得到他们使用 App 的习惯。

##### 内容分析：
###### 对用户平时浏览的内容，尤其是停留时间长、浏览次数多的内容进行分析，分析出用户对哪些内容感兴趣，比如，金融、娱乐、教育、体育、时尚、科技等。

#### 数据采集
##### [集搜客](http://www.gooseeker.com/)

##### [火车头采集器](http://www.locoy.com/)

##### [八爪鱼采集器](https://www.bazhuayu.com/)

##### 埋点采集数据
###### [代码埋点、可视化埋点、无埋点几种数据埋点方案的分析报告](https://blog.csdn.net/feishangbeijixing/article/details/86445704)

###### 友盟

###### Google Analysis

###### Talkingdata

#### Q&A
##### 最后，我们从现实生活中出发，打开你的手机，翻翻看你的微信通讯录，分析下你的朋友圈，都有哪些用户画像？如果你来给它设计标签，都有哪些种类需要统计呢。为了方便后续使用，你是如何将他们归类分组的？

#### Ref
##### [笔记](https://github.com/xiaomiwujiecao/DataAnalysisInAction)

### [[🍃 知识]] ~ [MySQL实操课程 - 阿里云大学](https://developer.aliyun.com/lesson_2209_22169)

### [[🍃 知识]] ~ [大数据系统基础-清华大学-学堂在线](https://next.xuetangx.com/course/THU08091000280/4230767?fromArray=search_result)
#### 数据类型
##### 结构化数据(关系)

##### 半结构化数据(XML)

##### 非结构化数据(文本)

### [[🍃 知识]] ~ 嵩天:数据分析与可视化
#### [Python数据分析与展示_中国大学MOOC(慕课)](https://www.icourse163.org/learn/BIT-1001870002?tid=1461061450#/learn/announce)

#### 

#### [Anaconda | 全球最受欢迎的数据科学平台](https://www.anaconda.com/)

#### NumPy 库
##### 主要用于数组计算

##### NumPy 的核心是数组（arrays），具体来说是多维数组（ndarrays）

#### Matplotlib 库
##### 数据可视化第三方库

#### Pandas 库
##### 分析数据 提取数据基本特征

##### 提供 高性能 易用 数据类型和分析工具

### [[🍃 知识]] ~ [吴恩达机器学习 - 网易云课堂](https://study.163.com/course/courseLearn.htm?courseId=1004570029#/learn/video?lessonId=1049052745&courseId=1004570029)

### [fast.ai · Making neural nets uncool again](https://www.fast.ai/)

### [[🍒 Python]]
#### [Python教程–真正的Python](https://realpython.com/)

### [概率论与数理统计-清华大学-学堂在线](https://www.xuetangx.com/course/THU07011000299/4230825?fromArray=search_result)

### [NeuHub京东人工智能开放平台-全球领先的AI技术提供商](https://neuhub.jd.com/)
#### [基于京东项目数据，培养行业TOP10%的数据分析师](https://neuhub.jd.com/promotion/course-bi?from=neuhub)

#### [京东商业数据分析可视化BI实训营-课程服务-京东创新平台-京东人工智能开放平台](http://neuhub.jd.com/market/course/398)

## 书单
### 业务知识
#### 《增长黑客》

#### 《精益数据分析》

#### 《深入浅出数据分析》

#### 《谁说菜鸟不会数据分析》

#### 《决战大数据 》

### python/爬虫
#### [[Book_《利用Python进行数据分析》]]

#### [Python Cookbook（第3版） (豆瓣)](https://book.douban.com/subject/26381341/)
##### [前言 — python3-cookbook 3.0.0 文档](https://python3-cookbook.readthedocs.io/zh_CN/latest/preface.html)

#### 《Python学习手册》

#### 《Python for everyone》

#### 《对比Excel，轻松学习Python数据分析》

#### 《Python3网络爬虫开发实战》

### 数学/统计学/概率论
#### 《看穿一切数字的统计学》

#### 《写给所有人的极简统计学》

#### [《概率论与数理统计》 (豆瓣)](https://book.douban.com/subject/2201479/)

#### 《统计基础》人大版本,

#### 《女士品茶》

#### 《统计陷阱》

#### 《漫画统计学入门》

#### 《机会的数学》

### SQL
#### 《Sql基础教程》

#### 《Sql进阶教程》

#### 《Hive编程指南》

### 《思维简史：从丛林到宇宙》

### 《数据挖掘：概念与技术》

### 《Pentaho Kettle解决方案》

### 《Small Data》

## 大咖
### 空白白白白:
#### https://www.zhihu.com/people/jiafeimao/activities

### 邹昕：
#### https://www.zhihu.com/people/xin_zou/activities

### 张溪梦：
#### https://www.zhihu.com/people/simonzhang1/activities

### 何明科：
#### https://www.zhihu.com/people/he-ming-ke/activities

### 秦路：
#### https://www.zhihu.com/people/qin-lu-17/activities

## 组织
### [京东AI在线实训营](http://aicourse.jd.com/#/online)

### [数据分析网 - 大数据、数据分析、数据挖掘和人工智能门户](https://www.afenxi.com/)

### [Data Application Lab](https://www.dataapplab.com/)

### [赛迪网_中国信息产业风向标](http://ccidnet.com/)

### [中国信息通信研究院](http://www.caict.ac.cn/)

### [中国电子信息产业发展研究院_赛迪集团_中国信息服务著名品牌](https://www.ccidgroup.com/)

### [大数据导航](http://hao.gsdata.cn/dsj/)

### [机器之心 | 企业人工智能服务](https://www.jiqizhixin.com/)

### [紫数 丨专注数据商业化的专业内容服务平台](http://www.zishu010.com/)

### [清数D-Lab »](http://www.ids.tsinghua.edu.cn/index.php/archives/category/qingshu-dlab)

### [清华大学数据科学研究院 »](http://www.ids.tsinghua.edu.cn/index.php)

### [大数据文摘 - 主页](https://study.163.com/provider/10146755/index.htm)

### [数据人网-数据人学习、交流和分享的平台](http://www.shujuren.org/)

### [数据分析网](https://www.afenxi.com)

### [大数据中国 | 关注数据产业_大数据资讯门户](https://www.bigdatas.cn/)

### [数据分析培训,全栈数据科学教育品牌—CDA数据分析师](https://www.cda.cn/)

### [Towards Data Science](https://towardsdatascience.com/)

## ---

## {{阅读 null}}
### [数据实战合辑：数据分析&数据产品&数据技术](https://mp.weixin.qq.com/s?__biz=MzI0OTEzNzYyOA==&mid=2650415497&idx=1&sn=7deb8c555c061d1c2593f01c762a886c&chksm=f198913ac6ef182c5a99b28c4886f16197539e4ebb58c19bc0137ea7d8a6a5dbd6c03faabd69&mpshare=1&scene=1&srcid=1221yaFXFjW8qZnjqEM7QNiD&sharer_sharetime=1608561820220&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.1.0.3004&platform=win#rd)

### [如何从0开始做大数据治理（上）](https://mp.weixin.qq.com/s?__biz=MzIxMzAxNzEwNQ==&mid=2648097648&idx=1&sn=afec5281e33c507045b18ead64f5967c&chksm=8f9f540eb8e8dd1873c5a40e085905d76182763ba26d495537961f989fc9ce6a8b6f36b3856d&mpshare=1&scene=1&srcid=12030tWhVm0Qlrp78jmOymsW&sharer_sharetime=1606995260051&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.31.3309&platform=win#rd)
#### **3. 组织协作出现**

#### 庞大的数据规模，纷问题乱的命名和存储，以及理不清的业务逻辑，让团队协同越来越难，推进大型项目需要参与的团队人数越来越多。体现在企业集中力量办大事的能力逐渐丧失。

#### **4. 数据孤岛开始出现**

#### 想要获得一项指标，找不同的人可以得到不同的查询结果，这其中出现的问题主要是口径对焦。不同的人对于业务的理解也并不相同，缺少统一的标准，这是很多公司发展过程中都存在的问题。数据不好找，找到不敢用、不能用，迫使业务只能选择重复建设资产，而重复建设资产更进一步加剧了数据不好找不好用的问题，形成了恶性循环，数据孤岛壁垒越垒越高。

#### 这一系列的问题如果任由其继续发展，数据对于业务只会变成鸡肋，甚至会成为企业的负债。

#### 某金融科技独角兽制定了三项核心规范：
##### ”数据资产必须先定义后研发”

##### ”数据资产不能重复建设”

##### ”应用资产依赖公共服务资产建设”。

### [数据工程师途径](https://awesomedataengineering.com/)

### [独家 | 每个业务分析专家应具备的9个关键技能](https://mp.weixin.qq.com/s?__biz=MzI1MjQ2OTQ3Ng==&mid=2247514079&idx=1&sn=cbeecc89fa1cd82b372fd7ca8e08743a&chksm=e9e1be54de963742dc095f09c8869f9340ffcf84104687c77106a9d0f4f76f6bb8639fcda118&mpshare=1&scene=1&srcid=0928Hmz1ZEN4h7kaLkTykJkj&sharer_sharetime=1601296799067&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.31.2998&platform=win#rd)

### [收藏 | 超详细数据分析学习路线,菜鸟也可以入门!-技术圈](https://jishuin.proginn.com/p/763bfbd23357) 

### [100天学习计划 | 一份详实的数据科学指南 | 数据分析网](https://www.afenxi.com/80109.html)

### [统计计量丨统计学公开课大盘点（附下载）](https://mp.weixin.qq.com/s?__biz=MzI1MjQ2OTQ3Ng==&mid=2247513124&idx=2&sn=82c6004d6e7740a2209bc042330179e2&chksm=e9e1bdafde9634b9502c825f0593af6208735424f3c68fdc56b1b5c6528e9b508700cc645545&mpshare=1&scene=1&srcid=0919cbVMtS2PmS27fbPhsNLs&sharer_sharetime=1600514865309&sharer_shareid=e9e2dce311463a0fb35decab135a67ca#rd)

### [独家 | 在数据科学中需要多少数学技能？（附链接）](https://mp.weixin.qq.com/s?__biz=MzI1MjQ2OTQ3Ng==&mid=2247512963&idx=1&sn=1beb298ad818561346ba6428e8f61700&chksm=e9e1ba08de96331e26e1c80c1fab7d0caa4bc20ff179fe56d9c88b0321e5bd7249a5190cd414&mpshare=1&scene=1&srcid=0916zYcF8YUsp48NoAH9RXDL&sharer_sharetime=1600212419585&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.30.2006&platform=win#rd)

### [数据分析招聘要求：熟练SQL！| 精简版复习大纲送给大家！](https://mp.weixin.qq.com/s?__biz=MzU5NDgyMjc0OQ==&mid=2247483986&idx=1&sn=e4f119fb9948f3ece6b88d0f69b6460b&chksm=fe7a1160c90d9876fa2feea4152765137487bcd2c7a64e6d37215a414080e1b05a28f821d1c3&scene=21#wechat_redirect)

### [Numpy、Pandas、SciPy、Scikit-Learn、Matplotlib的关系以及学习资料](https://blog.csdn.net/u014410989/article/details/89947128)

### [CDA认证中心](https://www.cdaglobal.com/article/83.html)

### [大数据DT_数据分析专栏](https://mp.weixin.qq.com/mp/homepage?__biz=MzI5OTk5OTM2Mw==&hid=16&sn=c75c9a6da01fd906d37da5c778db0502&st=16BBB8D1C98866DC6A320EE987FEDBBEC6EE4A86D0AA52E66FB1EE06A5A797F4639F06F36D212520305B7F47AFEE2170A137D5BA551F8E4F2A939A8BC519EA8573BE3A11BCBB18C4043E729D8525B2B764F011E3DA112796173A4DCE51DAFD20814AA9AF3C347AFC9C384CC9A850321F66330EAEEA2EC857A064A59BAEFFE401E32A337F873F736481A6DEBC9959936C&vid=1688850277420567&cst=4E35C58050022FE6AB38986FC8771E5260226FA9F4951DEC800F08BDBB93CF9F6FCE66A575C2976DF630F826D457D66E&deviceid=38a43bd8-f545-4389-b05b-291e551dc1c0&version=3.0.30.2006&platform=win)

### [大数据DT_数据可视化专栏](https://mp.weixin.qq.com/mp/appmsgalbum?action=getalbum&album_id=1330693976885772289&__biz=MzI5OTk5OTM2Mw==&st=C01AAB5A86F35009B5A8F8E0520D8B8E148EB782760B9348805E1BD6195CB2285D96BAA3FE813E5E51A441E090C4576A2C8ACF6E76DB9153C5FDE056F2A72A7056F09B4A265BA86B0BC595C611597748836333C8613306C38240AEF9E827AA3342361E6F63537388D01A9DF303ECCDC0EF50EE9AE903DEE2F5E5AD1EFCE3F93E3FBFDA520138DB23948CA3DC525A3FF2&vid=1688850277420567&cst=68E60DBBA7AE66AECA825D06C11A7F22B66DDFA280F33501AC58F9A83CC0BA898EA78E9F3A232C865E9C9D16578FB04B&deviceid=38a43bd8-f545-4389-b05b-291e551dc1c0&version=3.0.30.2006&platform=win#wechat_redirect)

### [大数据DT_数据库专栏](https://mp.weixin.qq.com/mp/appmsgalbum?action=getalbum&album_id=1329233323335565312&__biz=MzI5OTk5OTM2Mw==&st=DDB00BA11D2D8E02F7EF21DFA3115E60B7A4306D5F87B81FCF62B87C9F191E2CCAE1DFCB9F612392E743BCC1CFAF4AA5F598460934AAA037184E1D5FCDE4B127E05BE2E46F4C4C6DADB88AB3F0FB8AFADAEDCC8EDA5B03BFE1DB4E18CB6D04FB49E036FDBBBCD043F1124260CE40F55CF50140E7B79B5756806875BB12EE90A1ECFFA34D7513C8904A105640331A2ED0&vid=1688850277420567&cst=B61E59418F64EE0E54D715A353491A9FD6F0A8C2368568221076493DD83237E816B5DA855BCFE2E09560BF58C281FD73&deviceid=38a43bd8-f545-4389-b05b-291e551dc1c0&version=3.0.30.2006&platform=win#wechat_redirect)

### [MongoDB从立地到成佛(介绍、安装、增删改查)](https://mp.weixin.qq.com/s?__biz=Mzg2MTE1NjA2Mg==&mid=2247484735&idx=1&sn=15bdbc32458f53fe2829abba1b59e827&chksm=ce1a228ef96dab988e6a00926ad8d995f0fc32a5f54778bd1e8c4621bdd3671d53978728a39e&mpshare=1&scene=1&srcid=0922yueNfy6dsvfYgnIqI89I&sharer_sharetime=1600731719992&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.30.2006&platform=win#rd)

### [用数据讲故事（三）](https://mp.weixin.qq.com/s?__biz=MzAxNTgzMDI5MA==&mid=2650664357&idx=1&sn=175efa12e3fbb0bfe59f13a918ac3671&chksm=83f751d8b480d8ce3526cdbccb99cded25cbc047537634a1a6507518b52bd9cd7c13b929d94e&mpshare=1&scene=1&srcid=0919IzvZjPXjF6NvBf62215D&sharer_sharetime=1600473551542&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.30.2006&platform=win&rd2werd=1#wechat_redirect)

### [清华刘云浩教授回复学生2000问，你想了解的人工智能问题可能都在这里](https://mp.weixin.qq.com/s?__biz=MzI1MjQ2OTQ3Ng==&mid=2247510573&idx=1&sn=818fad7e3aa64a6640112848543f761c&chksm=e9e1a3a6de962ab02b24a9405402107f1cc00ea466f91162efadd1606f6e86135b86270f0d8d&mpshare=1&scene=1&srcid=0823w5C9WzWB05ht8Ct1Yknc&sharer_sharetime=1598139101817&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&key=c8f5304565ebcc6d129d6f7ba9cbe83ebc4cc0cefbce820cf76880d3157bf3398bfdfcc68cc01bc0ba55ff3d426cd7e4504a107c644f28e5d60d6e3f6d0e7b1580cbbc1e2d0241e50d42a0ae69ebba49cd4c99e813ecca7c50f840b6c336c0938a3a81a0c6cfe5faaf218ba14c69850180517f901f3d7998b30ec364feeab778&ascene=1&uin=MTI0NTIwNjEzMQ%3D%3D&devicetype=Windows+10+x64&version=62090529&lang=zh_CN&exportkey=A6u9pT4ZCykL7Duh6UVUZ4Q%3D&pass_ticket=jtY5PT%2BqvETdEjLmiVHbtqWikNM2AKRxP5xGnnsB2%2Bl1OIyhXV3bt8M0PQxofa1w)

### [重磅干货丨数字冰雹大数据可视决策 技术解析](https://mp.weixin.qq.com/s?__biz=MzA5OTEyMTU5OQ==&mid=2247492206&idx=1&sn=95b30829705e43e3698e5a5653e82f30&chksm=908582bea7f20ba81b723d0d4247396131831d1b4058ba52eea6cb7a2debe273d8ecde49cf89&mpshare=1&scene=1&srcid=082657ju2WvjirGagQvppqsF&sharer_sharetime=1598446526840&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&key=055c38dd9efc48935c4e5a7dfbce19439b41de08e80e14d05f1b8a1ed51fd44cd22523bb44fd4f9968e796332687ebefe275b8cc7e21c837799f736e6de8357e07a7559678651e124faa66698dbc55690cf9650a410c5f1f0fe03c81a224e5d7f0cb09ab4133e05a7f0a6ef73c801ed569c5b4131742a2df69aebedf1f49a1ba&ascene=1&uin=MTI0NTIwNjEzMQ%3D%3D&devicetype=Windows+10+x64&version=62090529&lang=zh_CN&exportkey=A5OiuM8wu2YnWKr1VdAv6Qc%3D&pass_ticket=jtY5PT%2BqvETdEjLmiVHbtqWikNM2AKRxP5xGnnsB2%2Bl1OIyhXV3bt8M0PQxofa1w)

### [浅谈人工智能：现状、任务、构架与统一 | 正本清源](https://mp.weixin.qq.com/s?__biz=MzI3MTM5ODA0Nw==&mid=2247484058&idx=1&sn=0dfe92a0991294afba2514b137217a66&chksm=eac3276addb4ae7c6acbc6f9275bf8ad5dcefafab631b41905d9f78c01ae46ddde8b2d9e7b31&mpshare=1&scene=1&srcid=0820KcIUFqStIaBIeNFKmzt9&sharer_sharetime=1597885278664&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.27.2701&platform=win#rd)
#### 人工智能
##### （1）计算机视觉（暂且把模式识别，图像处理等问题归入其中）

##### （2）自然语言理解与交流（暂且把语音识别、合成归入其中，包括对话）

##### （3）认知与推理（包含各种物理和社会常识）

##### （4）机器人学（机械、控制、设计、运动规划、任务规划等）

##### （5）博弈与伦理（多代理人 agents 的交互、对抗与合作，机器人与社会融合等议题）。

##### （6）机器学习（各种统计的建模、分析工具和计算的方法）

#### 感知
##### 视觉

##### 语音

#### 认知

#### 推理

#### 学习

#### 执行

#### ---

#### 计算机视觉

#### 自然语言理解

#### 认知科学

#### 机器学习

#### 机器人学

### 数据驱动：组织行为是基于数据进行决策的，而不是凭主观直觉或个人经验。

### [招聘 | 贝恩高级数据分析组召集令](https://mp.weixin.qq.com/s?__biz=MzAxNzAxNjg2Nw==&mid=2650596299&idx=1&sn=ed19a1faf42a9a0250ab085b761f93e9&chksm=83e3b287b4943b91c112a0034aa12c3ee9133e92648355ee57e409200fa4d54412e4755954e6&mpshare=1&scene=1&srcid=0911fUspMK3ksgiPn18kG8VT&sharer_sharetime=1599834896018&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.30.2006&platform=win&rd2werd=1#wechat_redirect)

### [技术人最不该忽视可视化数据分析！ - InfoQ](https://www.infoq.cn/article/Q5B5BQcQV5SUjYbElB8p)

### [招募 | 《大数据实践课》课程实践企业合作项目](https://mp.weixin.qq.com/s?__biz=MzI1MjQ2OTQ3Ng==&mid=2247511582&idx=2&sn=ccc91a4824a3d1e099cb225b4db17507&chksm=e9e1a795de962e83fc0f4e773a63da90a8c41c22ab8a932d59b8bf300131fecbc76cffedf4a0&mpshare=1&scene=1&srcid=08292nI1QTEzQNRb5qJi2HAw&sharer_sharetime=1598698490671&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.27.2701&platform=win&rd2werd=1#wechat_redirect)
#### 熟悉典型大数据工具与平台的特性

#### 掌握大数据处理的基本开发方式

#### 巩固和加深大数据分析的基础知识

#### 完成一个 数据分析系统架构的设计与实现的 项目

### [数字化转型的7个错误认知](https://mp.weixin.qq.com/s?__biz=MzI1MzcwMDg2MA==&mid=2247488069&idx=1&sn=10a314ba8e2bd3f823d39721f668c7a9&chksm=e9d12dd6dea6a4c03a452289f7cb57ee7e4b5d0843096502a5ced613f6a58754e8306184e7d5&mpshare=1&scene=1&srcid=0827Fh5dD8IdD5gxTf9HJrCf&sharer_sharetime=1598522451222&sharer_shareid=e9e2dce311463a0fb35decab135a67ca&version=3.0.27.2701&platform=win&rd2werd=1#wechat_redirect)
