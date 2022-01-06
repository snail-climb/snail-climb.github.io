# Markdown语法

> Markdown（美 /ˈmɑːrkdaʊn/）是一种轻量级标记语言，排版语法简洁，让人们更多地关注内容本身而非排版。它使用易读易写的纯文本格式编写文档，可与HTML混编，可导出 HTML、PDF 以及本身的 .md 格式的文件。因简洁、高效、易读、易写，Markdown被大量使用，如Github、Wikipedia、简书等。

## 1. 标题语法

> 创建标题：要在标题内容前添加`#`，`#`的数量代表标题的级别（一级标题级别最高，六级标题级别最低）。

> 不同的Markdown应用程序处理`#`和标题之间的空格方式并不一致，为了兼容考虑，用一个空格在`#`和标题之间进行分隔。

**源码**：
```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

**效果**：
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

## 2. 段落语法

> 创建段落：通过换行的方式，将文本内容分段。

会当凌绝顶，
一览众山小。

## 3. 换行语法

> 四种方式：
> 1. 在行的末尾添加两个或多个空格，然后键入回车键。
> 2. 使用HTML的`<br>`标签。
> 3. 在行的末尾添加反斜杠`\`。
> 4. 在行的末尾不添加任何内容，只须键入回车键。

桃花潭水深千尺，
不及汪伦送我情。

## 4. 强调语法

> 通过将文本设置为粗体或斜体来强调其重要性。
> 设置斜体：用`*`包裹文本内容。
> 设置粗体：用`**`包裹文本内容。
> 既设置斜体又设置粗体：用`***`包裹文本内容。

| 强调样式  | 源码                 | 效果               |
| --------- | -------------------- | ------------------ |
| 斜体      | `*Hello,World!*`     | *Hello,World!*     |
| 粗体      | `**Hello,World!**`   | **Hello,World!**   |
| 斜体+粗体 | `***Hello,World!***` | ***Hello,World!*** |

## 5. 引用语法

1. 块引用：在段落前添加`>`符号。

**源码**：
```markdown
> 我翻开历史一查，这历史没有年代，歪歪斜斜的每叶上都写着“仁义道德”几个字。我横竖睡不着，仔细看了半夜，才从字缝里看出字来，满本都写着两个字是“吃人”！
```

**效果**：
> 我翻开历史一查，这历史没有年代，歪歪斜斜的每叶上都写着“仁义道德”几个字。我横竖睡不着，仔细看了半夜，才从字缝里看出字来，满本都写着两个字是“吃人”！

2. 多个段落的块引用：块引用可以包含多个段落。

**源码**：
```markdown
> 落霞与孤鹜齐飞
> 
> 秋水共长天一色
```

**效果**：
> 落霞与孤鹜齐飞
> 
> 秋水共长天一色

3. 嵌套块引用：块引用可以嵌套，在要嵌套的段落前添加`>>`符号。

**源码**：
```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
> 
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

**效果**：
> Dorothy followed her through many of the beautiful rooms in her castle.
> 
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

4. 带有其它元素的块引用：块引用可以包含其他Markdown格式的元素，但并非所有元素都可以使用，需要进行实验以查看哪些元素有效。

**源码**：
```markdown
> #### The quarterly results look great!
> 
> - Revenue was off the chart.
> - Profits were higher than ever.
> 
>  *Everything* is going according to **plan**.
```

**效果**：
> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.

## 6. 列表语法

1. 创建有序列表：在每个列表项前添加数字并紧跟一个英文句点（数字不必按数学顺序排列，但是列表应当以数字 1 起始）。

**有序列表源码**：
```markdown
1. First item
2. Second item
3. Third item
或
1. First item
1. Second item
1. Third item
```

**有序列表效果**：
1. First item
2. Second item
3. Third item

2. 创建无序列表：在每个列表项前添加`-`、`*`或`+`，通过缩进，可创建嵌套列表。

**无序列表源码**：
```markdown
- First item
- Second item
- Third item
	- Indented item
	- Indented item
- Fourth item
```

**无序列表效果**：
- First item
- Second item
- Third item
	- Indented item
	- Indented item
- Fourth item

## 7. 代码语法

1. 将内容表示为代码，需要将其包裹在反引号（`）中。

	**源码**：
	``Use `code` in your Markdown file.``
	
	**效果**：
	Use `code` in your Markdown file.

2. 转义反引号：将内容包裹在双反引号（``）中。

3. 代码块：
	> Markdown基本语法允许将行缩进四个空格或一个制表符来创建代码块。
	> 围栏代码块(受保护的代码块)：将在代码块之前和之后的行上使用三个反引号（```）或三个波浪号（~~~）。

```
public static void main() {
	System.out.println("Hello World!");
}
```

语法高亮：在受防护的代码块之前的反引号旁，指定语言。

```java
public static void main() {
	System.out.println("Hello World!");
}
```

## 8. 分割线

> 创建分隔线：在单独一行上使用三个或多个星号`***`、`---`或`___`，并且不能包含其他内容

**源码**：

`***`
或
`---`
或
`___`

**效果**：

---

## 9. 链接语法

1. 链接文本放在中括号内，链接地址放在小括号内，链接title可选。
超链接语法代码：`[超链接显示名](超链接地址 "超链接title")`
对应的HTML代码：`<a href="超链接地址" title="超链接title">超链接显示名</a>`

	**源码**：
	`[点击跳转至作者博客](https://blog.csdn.net/weixin_45880773 "超链接标题")`
	
	**效果**：
	[点击跳转至作者博客](https://blog.csdn.net/weixin_45880773 "超链接标题")

2. 使用尖括号可以更方便地把URL或Email地址变成可点击的链接。

	**源码**：
	`<https://gitee.com/snail-climb>`
	`<daning@example.com>`
	
	**效果**：
	<https://gitee.com/snail-climb>
	<daning@example.com>

3. 强调链接, 在链接语法前后增加星号。
	要将链接表示为代码，在方括号中对内容添加反引号。

	**源码**：
	`This is my **[Gitee](https://gitee.com/snail-climb)**.`
	`[`code`](#code).`
	
	**效果**：
	This is my **[Gitee](https://gitee.com/snail-climb)**.
	[`code`](#code).

## 10. 图片语法

1. 图片替代文本放在中括号内，链接地址放在小括号内，图片title可选。
	图片语法代码：`![图片alt](图片链接 "图片title")`
	对应的HTML代码：`<img src="图片链接" alt="图片alt" title="图片title">`

	**源码**：
	
	`![头像](./images/photo_1.jpg "图片标题")`
	
	图片链接：
	
	`[![头像](./images/photo_1.jpg)](https://blog.csdn.net/weixin_45880773)`
	
	**效果**：
	
	![头像](./images/photo_1.jpg "图片标题")
	
	图片链接：
	
	[![头像](./images/photo_1.jpg)](https://blog.csdn.net/weixin_45880773)

## 11. 表格

**源码**：

```markdown
| 姓名 | 性别 | 年龄 |
| ---- | ---- | ---- |
| 张三 | 男   | 22   |
| 李四 | 男   | 18   |
| 王五 | 男   | 25   |
```

**效果**：

| 姓名 | 性别 | 年龄 |
| ---- | ---- | ---- |
| 张三 | 男   | 22   |
| 李四 | 男   | 18   |
| 王五 | 男   | 25   |

