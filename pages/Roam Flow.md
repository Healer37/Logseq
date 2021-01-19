---
title: Roam Flow
---

## **Roam样式**
### sidebar对应^^项目^^，主界面对应^^资料^^
#### sidebar不变，且可以在右侧打开^^多个项目同时进行^^；主界面可以通过^^搜索^^不断切换到对应界面

### 字体大小（Ctrl-1,2,3）体现^^层级结构^^
#### 可以使用^^emoji表情^^对不同层级进行**突出显示**

### ^^高亮^^、**加粗**、斜体体现^^内容整理^^
#### 高亮针对句子，即^^联系^^

#### 加粗针对^^概念^^

#### 斜体针对^^例子^^

## **看板功能与GTD**
### 看板功能对应^^子项目^^层面

### GTD对应子项目下的^^任务^^

## **阅读笔记流**
### 利用**Roam样式**建立^^全文Page^^

### 利用 **Block Reflences** 引用原文，并在对应原文下面建立^^# LN^^标签

### 利用 **Query命令**收集所有# LN内容，并集中在^^# Literature Notes^^标签下

### 利用**QA方式**整理来自# Literature Notes的内容，并集中在^^# Permanent Notes^^标签下

## **快捷键**
### win+shift :打开Line References

### alt+shift :打开Line Graph

### **roam42快捷键**
#### Alt-Shift-H：导航

#### Alt+L：打开/关闭实时预览

#### Ctrl-Shift-H ：搜索列表

#### ^^Alt-Shift-,: 打开独立Dailynote窗口^^

#### Alt-Shift-.:打开英英词典
    
    

#### ^^Alt-Shift-D : 将中文日期字义转换为具体日期Page^^（省去了查日历的时间）

#### ^^Alt-Shift-J : 跳转到日期选择界面^^

#### Alt-Shift-Up Arrow/Down Arrow: 上下移动Block

#### Alt-m： 打开Markdown模式

#### Shift-Up-Up __or__ Shift-Down-Down ：上下选择多个Block

#### Ctrl-Shift-A ：选择当前Page的所有Block

#### ^^Ctrl-J / Ctrl-K ：搜索框内上下选择可选项^^

### Alt-Shift-\: 打开左侧Sidebar

### Alt-Shift-/: 打开右侧Sidebar

### 页面快捷键
#### Fn 键+方向左键 Home 键（页首）

#### Fn 键+方向上键 PgUp 键

#### Fn 键+方向下键 PgDn 键

#### Fn 键+方向右键 End 键（页尾）

## **引用功能**
### **内部引用**
#### **区块（block）层面**
##### ^^双括号^^和^^embed函数^^的区别在于：双括号无法直接修改^^现在位置引用的内容^^，需要跳转到^^原位置修改原内容^^，但是embed函数可以直接同步修改现在位置引用的内容和原位置的原内容

#### **页面(page)层面**
##### ^^mention函数^^和^^query函数^^的区别在于mention函数只能引用^^一个页面^^，而query函数只能引用^^多个页面,并通过and、or等函数限定范围^^
###### **mention函数**
####### 显示的内容表示主界面下面的链接界面（报包含加双括号和未加双括号部分）

###### **query函数**
####### `{ {[ [query] ]: {or: [ [ex-B] ] [ [ex-C] ]}} {not : [ [query] ]}}`

####### Query命令的筛选功能

####### ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FHealer374%2FxnNK4jOOrz.png?alt=media&token=2f257c3f-057a-44d7-8472-997ab7c8d5f2)

### **外部引用**
#### **书籍**
##### 微信读书
###### 直接在^^当前页面复制链接^^并贴到roam或者用iframe函数嵌入roam

##### kindle
###### 高亮、注释导出

#### **文字**
##### ^^原文数据量较大^^，所以可以先放在^^幕布或者notion^^，然后再把用^^Link to Text Fragment插件^^生成的链接贴到roam或者用iframe函数嵌入roam
###### [幕布](https://share.mubu.com/doc/4UCV8L5RNIz)

###### [notion](https://www.notion.so/e84c01ade6d24014a475f6bf65244272)

#### **文件**
##### 本地文件上传到天翼云盘，然后在^^天翼云盘^^网页版生成文件的链接，把链接贴到roam里
###### https://cloud.189.cn/t/fYvuqq7rmAfi

###### [alias函数 变成可点击的URL链接](https://cloud.189.cn/t/fYvuqq7rmAfi)

##### 上传到notion，并在notion生成链接贴到roam

#### **PDF**
##### ^^本地PDF^^：用**chrome**打开（无法编辑），然后生成链接，把链接贴到roam或者用**iframe函数**嵌入roam
###### [2020注会《会计》晨陽锦囊笔记.pdf](chrome-extension://oemmndcbldboiebfnladdacbdfmadadm/file:///D:/%E5%A4%A9%E7%BF%BCTB/%E9%BB%98%E8%B0%A6/0406.CPA%E8%80%83%E8%AF%95%E8%B5%84%E6%96%99/2020%E6%B3%A8%E4%BC%9A%E3%80%8A%E4%BC%9A%E8%AE%A1%E3%80%8B%E6%99%A8%E9%99%BD%E9%94%A6%E5%9B%8A%E7%AC%94%E8%AE%B0.pdf)
####### {{iframe https}}

##### ^^网页PDF^^：直接将链接贴入roam或者用**iframe函数**嵌入roam

#### **网页**
##### **iframe函数**（嵌入roam，直接在roam上查看）
###### {{iframe https}}

## **流程图 Mermaid**
### [实时绘制链接Mermaid Live Editor](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggVERcbiAgQVtDaHJpc3RtYXNdIC0tPnxHZXQgbW9uZXl8IEIoR28gc2hvcHBpbmcpXG4gIEIgLS0-IEN7TGV0IG1lIHRoaW5rfVxuICBDIC0tPnxPbmV8IERbTGFwdG9wXVxuICBDIC0tPnxUd298IEVbaVBob25lXVxuICBDIC0tPnxUaHJlZXwgRltmYTpmYS1jYXIgQ2FyXVxuXHRcdCIsIm1lcm1haWQiOnsidGhlbWUiOiJkZWZhdWx0In19)

### #c:blue ^^ 流程图^^
#### {{mermaid null}}
##### graph TD;
###### A-->B;

###### A-->C;

###### B-->D;

###### C-->D;

#### {{mermaid null}}
##### graph TD

###### A[Christmas] -->|Get money| B(Go shopping)

###### B --> C{Let me think}

###### C -->|One| D[Laptop]

###### C -->|Two| E[iPhone]

###### C -->|Three| F[fa:fa-car Car]
					

### #c:blue ^^ 序列图^^
#### {{mermaid null}}
##### sequenceDiagram
###### participant A

###### participant B

###### A->>C: Hello John, how are you?

###### loop Healthcheck
####### C->>C: Fight against hypochondria

###### end

###### Note right of C: Rational thoughts <br/>prevail!

###### C-->>A: Great!

###### C->>B: How about you?

###### B-->>C: Jolly good!

### #c:blue ^^ 行程图^^
#### {{mermaid null}}
##### journey
###### title My working day
####### section Go to work
######## Make tea: 5: Me

######## Go upstairs: 3: Me

######## Do work: 1: Me, Cat

####### section Go home
######## Go downstairs: 5: Me

######## Sit down: 5: Me

### #c:blue ^^甘特图 ^^
#### {{mermaid null}}
##### gantt
###### dateFormat  YYYY-MM-DD

###### title Adding GANTT diagram to mermaid

###### excludes weekdays 2014-01-10

###### section A section

###### Completed task:done,des1, 2014-01-06,2014-01-08

###### Active task:active,des2, 2014-01-09,3d

###### Future task:des3, after des2,5d

###### Future task2:des4, after des3,5d

### #c:blue ^^ 饼状统计图^^
#### {{mermaid null}}
##### pie title Pets adopted by volunteers
###### "Dogs" : 386

###### "Cats" : 85

###### "Rats" : 15					

## ^^从段中回到段首或者段尾^^
### win -> 1.Esc  2.方向左右键

## ^^原文显示功能^^
### :hiccup [:blockquote"<要输入的内容>"]
#### 此功能无法在内部对文本高亮和加粗，故一般适用于不需要高亮加粗的文本

### :hiccup [ :blockquote "第一行"[:br] "第二行" ]
#### 第一行与第二行之间用`[:br]`隔开

### :hiccup [:hr]

### ---

## **手写功能**
### :hiccup [ :blockquote "{{[[drawing]] null}}" ]

### `{{[[drawing]] null}}`

## ^^各级标题及正文样式^^
### 2018年抽凭

### 2018年抽凭

### 2018年抽凭

### **2018年抽凭**

### 2018年抽凭

## ^^层级颜色^^
### asg
#### adsg
##### asdg
###### ag
####### fsdfh
######## asg
######### asdga 
########## dgag
########### asg
############ sadg
############# asdga
############## asg
############### sdga
################ ag
################# g
################## ag
################### asdg
#################### 

## ^^工具相关图解^^
### ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FHealer372%2Fv9_K-dMC7u.png?alt=media&token=94107fdf-c924-4d0a-84ea-e4b261cb0e84)
