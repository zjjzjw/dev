# 基本语法
##  标题
- Markdown支持6种级别的标题，对应html标签 h1 ~ h6

# h1
## h2
### h3
#### h4
##### h5
###### h6
这是一级标题
===
这是二级标题
---

## 段落及区块引用
- Markdown其实就是一种易于编写的普通文本，只不过加入了部分渲染文本的标签而已。其最终依然会转换为html标签，因此使用Markdown分段非常简单，前后至少保留一个空行即可。

> 这段文字将被高亮显示...

## 插入链接或图片

[点击跳转至百度](http://www.baidu.com)
![图片](https://upload-images.jianshu.io/upload_images/703764-605e3cc2ecb664f6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 列表
* 黄瓜
* 玉米
* 茄子

+ 黄瓜
+ 玉米
+ 茄子

- 黄瓜
- 玉米
- 茄子

1. 黄瓜
2. 玉米
3. 茄子

如果在单一列表项中包含了多个段落，为了保证渲染正常，*与段落首字母之间必须保留四个空格
*    段落一

     小段一
*    段落二

     小段二

如果在列表中加入了区块引用，区域引用标记符也需要缩进4个空格
* 段落一
    > 区块标记一
* 段落二
    > 区块标记二


## 分隔线
***
---

## 强调
*这里是斜体*
_这里是斜体_

**这里是加粗**
__这里是加粗__

## 插入代码块
```
fun (x: Int, y: Int): Int {
  return x + y
}
```

## 插入表格
使用 | 来分隔不同的单元格，使用 - 来分隔表头和其他行。
为了美观，可以使用空格对齐不同行的单元格，并在左右两侧都使用 | 来标记单元格边界。
在表头下方的分隔线标记中加入 :，即可标记下方单元格内容的对齐方式。
- :--- 代表左对齐
- :--: 代表居中对齐
- ---: 代表右对齐

表头|条目一|条目二
:---:|:---:|:---:
项目|项目一|项目二

| 表头 | 左对齐 | 右对齐 | 居中对齐 |
| ---- | :---- | ----: | :----: |
| 单元格| 单元格 | 单元格 | 单元格 |
| 单元格| 单元格 | 单元格 | 单元格 |




## 特殊符号处理
Markdown使用反斜杠\插入语法中用到的特殊符号。在Markdown中，主要有以下几种特殊符号需要处理：
```
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
```

## 如何给文字上色
先用Markdown编辑完成
导出为html，在需要上色的部分手动添加标签

<font color='#ff0000'>ssss</font>
<font color='#ff00ff'>ssss</font>
<font color='#fffc00'>ssss</font>
<font color='#ff0013'>ssss</font>
<font color='red'>ssss</font>
<font color='orange'>ssss</font>
<font color='yellow'>ssss</font>
<font color='green'>ssss</font>
<font color='Cyan'>ssss</font>
<font color='blue'>ssss</font>
<font color='violet'>ssss</font>

保存即可。

