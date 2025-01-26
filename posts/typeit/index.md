# 文档教程 Typeit


# 主题文档 - 扩展 Shortcode - typeit


`typeit` shortcode 基于 [TypeIt](https://typeitjs.com/) 提供了打字动画。

&lt;!--more--&gt;

只需将你需要打字动画的内容插入 `typeit` shortcode 中即可。

## 1 简单内容 {#simple-content}

允许使用 `Markdown` 格式的简单内容，并且 **不包含** 富文本的块内容，例如图像等等……

一个 `typeit` 示例：

```go-html-template
{{&lt;/* typeit */&gt;}}
这一个带有基于 [TypeIt](https://typeitjs.com/) 的 **打字动画** 的 *段落*……
{{&lt;/* /typeit */&gt;}}
```

呈现的输出效果如下：

{{&lt; typeit &gt;}}
这一个带有基于 [TypeIt](https://typeitjs.com/) 的 **打字动画** 的 *段落*……
{{&lt; /typeit &gt;}}

另外，你也可以自定义 **HTML 标签**.

一个带有 `h4` 标签的 `typeit` 示例：

```go-html-template
{{&lt;/* typeit tag=h4 */&gt;}}
这一个带有基于 [TypeIt](https://typeitjs.com/) 的 **打字动画** 的 *段落*……
{{&lt;/* /typeit */&gt;}}
```

呈现的输出效果如下：

{{&lt; typeit tag=h4 &gt;}}
这一个带有基于 [TypeIt](https://typeitjs.com/) 的 **打字动画** 的 *段落*……
{{&lt; /typeit &gt;}}

## 2 代码内容 {#code-content}

代码内容也是允许的，并且通过使用参数 `code` 指定语言类型可以实习语法高亮。

一个带有 `code` 参数的 `typeit` 示例：

```go-html-template
{{&lt;/* typeit code=java */&gt;}}
public class HelloWorld {
    public static void main(String []args) {
        System.out.println(&#34;Hello World&#34;);
    }
}
{{&lt;/* /typeit */&gt;}}
```

呈现的输出效果如下：

{{&lt; typeit code=java &gt;}}
public class HelloWorld {
    public static void main(String []args) {
        System.out.println(&#34;Hello World&#34;);
    }
}
{{&lt; /typeit &gt;}}

## 3 分组内容 {#code-content}

默认情况下，所有打字动画都是同时开始的。
但是有时你可能需要按顺序开始一组 `typeit` 内容的打字动画。

一组具有相同 `group` 参数值的 `typeit` 内容将按顺序开始打字动画。

一个带有 `group` 参数的 `typeit` 示例：

```go-html-template
{{&lt;/* typeit group=paragraph */&gt;}}
**首先**, 这个段落开始
{{&lt;/* /typeit */&gt;}}

{{&lt;/* typeit group=paragraph */&gt;}}
**然后**, 这个段落开始
{{&lt;/* /typeit */&gt;}}
```

呈现的输出效果如下：

{{&lt; typeit group=paragraph &gt;}}
**首先**, 这个段落开始
{{&lt; /typeit &gt;}}

{{&lt; typeit group=paragraph &gt;}}
**然后**, 这个段落开始
{{&lt; /typeit &gt;}}




---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/typeit/  

