# 測試測試測試


这篇文章提供了可以在 Hugo 的文章中使用的基本 Markdown 语法示例.

<!--more-->


<https://assemble.io>

<contact@revolunet.com>

[Assemble](https://assemble.io)

输出的 HTML 看起来像这样:

```html
<a href="https://assemble.io">https://assemble.io</a>
<a href="mailto:contact@revolunet.com">contact@revolunet.com</a>
<a href="https://assemble.io">Assemble</a>
```

### 添加一个标题

```markdown
[Upstage](https://github.com/upstage/ "Visit Upstage!")
```

呈现的输出效果如下 (将鼠标悬停在链接上，会有一行提示):

[Upstage](https://github.com/upstage/ "Visit Upstage!")

输出的 HTML 看起来像这样:

```html
<a href="https://github.com/upstage/" title="Visit Upstage!">Upstage</a>
```

### 定位标记

定位标记使你可以跳至同一页面上的指定锚点. 例如, 每个章节:

```markdown
## Table of Contents
  * [Chapter 1](#chapter-1)
  * [Chapter 2](#chapter-2)
  * [Chapter 3](#chapter-3)
```

将跳转到这些部分:

```markdown
## Chapter 1 <a id="chapter-1"></a>
Content for chapter one.

## Chapter 2 <a id="chapter-2"></a>
Content for chapter one.

## Chapter 3 <a id="chapter-3"></a>
Content for chapter one.
```

{{< admonition >}}
定位标记的位置几乎是任意的. 因为它们并不引人注目, 所以它们通常被放在同一行了.
{{< /admonition >}}

## 12 脚注

脚注使你可以添加注释和参考, 而不会使文档正文混乱.
当你创建脚注时, 会在添加脚注引用的位置出现带有链接的上标编号.
读者可以单击链接以跳至页面底部的脚注内容.

要创建脚注引用, 请在方括号中添加插入符号和标识符 (`[^1]`).
标识符可以是数字或单词, 但不能包含空格或制表符.
标识符仅将脚注引用与脚注本身相关联 - 在脚注输出中, 脚注按顺序编号.

在中括号内使用插入符号和数字以及用冒号和文本来添加脚注内容 (`[^1]：这是一段脚注`).
你不一定要在文档末尾添加脚注. 可以将它们放在除列表, 引用和表格等元素之外的任何位置.

```markdown
这是一个数字脚注[^1].
这是一个带标签的脚注[^label]

[^1]: 这是一个数字脚注
[^label]: 这是一个带标签的脚注
```

这是一个数字脚注[^1].

这是一个带标签的脚注[^label]

[^1]: 这是一个数字脚注
[^label]: 这是一个带标签的脚注

## 13 图片

图片的语法与链接相似, 但包含一个在前面的感叹号.

```markdown
![Minion](https://octodex.github.com/images/minion.png)
```

![Minion](https://octodex.github.com/images/minion.png)

或者:

```markdown
![Alt text](https://octodex.github.com/images/stormtroopocat.jpg "The Stormtroopocat")
```

![Alt text](https://octodex.github.com/images/stormtroopocat.jpg "The Stormtroopocat")

像链接一样, 图片也具有脚注样式的语法:

```markdown
![Alt text][id]
```

![Alt text][id]

稍后在文档中提供参考内容, 用来定义 URL 的位置:

```markdown
[id]: https://octodex.github.com/images/dojocat.jpg  "The Dojocat"
```

[id]: https://octodex.github.com/images/dojocat.jpg  "The Dojocat"

{{< admonition tip >}}
**DoIt** 主题提供了一个包含更多功能的 [图片的 shortcode](../theme-documentation-extended-shortcodes#image).
{{< /admonition >}}

