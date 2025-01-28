# 文档教程


本教程演示基本的编辑技巧，以供查询  

&lt;!--more--&gt;
## 文章自定义属性
[查看自定义属性](https://fixit.lruihao.cn/zh-cn/documentation/content-management/introduction/#front-matter &#34;Front Matter&#34;)

## Markdown 基础语法
### 核心操作 
#### 注释
``` md
&lt;!-- 这是一段注释 --&gt;
```
#### 加粗
两个*包围  
```md
**渲染为粗体**
__渲染为粗体__
```
效果如下：  
**渲染为粗体**  
__渲染为粗体__  

#### 斜体
一个*包围   
用于强调带有斜体的文本片段。  
以下文本片段被 渲染为斜体。  
```md
*渲染为斜体*  
_渲染为斜体_
```
*渲染为斜体*  
_渲染为斜体_  

#### 删除线
两个~包围  
以下文本片段被 渲染为删除线。
```md
~~ 我是删除线 ~~
```
~~我是删除线~~
### 核心组合使用
加粗，斜体，和删除线可以 组合使用  
下面一段代码渲染效果如下 ：
```md
**_~~我加粗倾体然后被删除了~~_**
``` 
**_~~我加粗倾体然后被删除了~~_**  

## Emoji表情符号
这部分内容在 [Emoji]({{&lt; ref &#34;emoji&#34; &gt;}} &#34;Emoji表情符号&#34;) 中介绍。  


## Markdown 扩展语法 (Fixit风格)
### 警示
#### 基本警示(简单用法)
```md
&gt; [!NOTE]
&gt; 突出显示用户应考虑的信息，即使只是浏览也应考虑。

&gt; [!TIP]
&gt; 可选信息，可帮助用户取得更大的成功。

&gt; [!IMPORTANT]
&gt; 用户成功所需的关键信息。

&gt; [!WARNING]
&gt; 由于存在潜在风险，需要用户立即关注的关键内容。

&gt; [!CAUTION]
&gt; 操作的潜在负面后果。
```
呈现的效果如下：
&gt; [!NOTE]
&gt; 突出显示用户应考虑的信息，即使只是浏览也应考虑。

&gt; [!TIP]
&gt; 可选信息，可帮助用户取得更大的成功。

&gt; [!IMPORTANT]
&gt; 用户成功所需的关键信息。

&gt; [!WARNING]
&gt; 由于存在潜在风险，需要用户立即关注的关键内容。

&gt; [!CAUTION]
&gt; 操作的潜在负面后果。  

你甚至可以省略正文来创建仅标题的警示  
&gt; [!TIP] 仅标题的警示

#### 可折叠警示(复杂用法)
你可以通过在类型标识符后直接添加加号（&#43;）或减号（-）来使警示可折叠。  
```md
&gt; [!WARNING]&#43; 辐射危害
&gt; 请勿在没有防护装备的情况下接近或操作。

&gt; [!QUESTION]- 警示可以折叠吗？
&gt; 是的！在可折叠警示中，内容在折叠时被隐藏。
```
&gt; [!WARNING]&#43; 辐射危害
&gt; 请勿在没有防护装备的情况下接近或操作。

&gt; [!QUESTION]- 警示可以折叠吗？
&gt; 是的！在可折叠警示中，内容在折叠时被隐藏。

#### 嵌套警示
```md
&gt; [!question] 警示可以嵌套吗？
&gt; &gt; [!todo] 可以！它们可以。
&gt; &gt; &gt; [!example] 你甚至可以使用多层嵌套。
```
&gt; [!question] 警示可以嵌套吗？
&gt; &gt; [!todo] 可以！它们可以。
&gt; &gt; &gt; [!example] 你甚至可以使用多层嵌套。

### 任务
要创建任务列表，请在每个列表项前添加一个短横线和空格，然后跟上 [ ]  
```md
- [x] 这是一个已完成的任务。
- [ ] 这是一个未完成的任务。
```
- [x] 这是一个已完成的任务。
- [ ] 这是一个未完成的任务。
你可以在括号内使用任何字符来标记任务为已完成或其他状态  
```md
- [ ] 未完成
- [x] 已完成
- [/] 进行中
- [-] 已取消
- [&lt;] 已计划
- [&gt;] 已重新计划
- [!] 重要
- [?] 问题
```
- [ ] 未完成
- [x] 已完成
- [/] 进行中
- [-] 已取消
- [&lt;] 已计划
- [&gt;] 已重新计划
- [!] 重要
- [?] 问题
&gt;[!WARNING]- 如何开启 Hugo 扩展语法
&gt;下划线、标记文本、下标 和 上标 语法默认关闭，需更新 Hugo 版本到 0.128.0 以上且开启以下的配置：
&gt;```md
&gt;[markup]
&gt;  [markup.goldmark]
&gt;    [markup.goldmark.extensions]
&gt;      strikethrough = false
&gt;      # https://gohugo.io/getting-started/configuration-markup/#extras
&gt;      [markup.goldmark.extensions.extras]
&gt;        [markup.goldmark.extensions.extras.delete]
&gt;          enable = true
&gt;        [markup.goldmark.extensions.extras.insert]
&gt;          enable = true
&gt;        [markup.goldmark.extensions.extras.mark]
&gt;          enable = true
&gt;        [markup.goldmark.extensions.extras.subscript]
&gt;          enable = true
&gt;        [markup.goldmark.extensions.extras.superscript]
&gt;          enable = true
&gt;```


### 标记文本
Hugo 支持一种 标记文本 Markdown 扩展语法：  
```md
==FixIt== 是一个很棒的 Hugo 主题！
```
==FixIt== 是一个很棒的 Hugo 主题！

### 下划线
```md
FixIt 主题的作者是 &#43;&#43;Lruihao&#43;&#43;。
```
FixIt 主题的作者是 &#43;&#43;Lruihao&#43;&#43;。

### 上标
```md
2^10^ 等于 1024。
```


下面是Fixit扩展的语法
```md
&gt; [!NOTE] FixIt
&gt; 一个简洁、优雅且高效的 Hugo 主题。
```
&gt; [!NOTE] FixIt
&gt; 一个简洁、优雅且高效的 Hugo 主题。
&gt; 
### 打字机效果
这部分内容在 [Typeit]({{&lt; ref &#34;typeit&#34; &gt;}} &#34;typeit使用介绍&#34;) 中介绍。  


### Font Awesome

FixIt 主题使用 Font Awesome V6 作为图标库。 你同样可以在文章中轻松使用这些图标。

从 [Font Awesome](https://fontawesome.com/icons?d=gallery) 网站 上获取所需的图标 class。

真开心！→ :(fa-solid fa-pen-nib):   :(fa-solid fa-star):  :(fa-solid fa-paperclip):  

### emoji表情
真开心！:joy:   → [表情代号查询](https://fixit.lruihao.cn/zh-cn/guides/emoji-support/)

### Shortcodes

{{&lt; admonition tips &gt;}}
The quick brown fox jumps over the lazy dog.
{{&lt; /admonition &gt;}}

#### mapbox

这部分内容在 [mapbox]({{&lt; ref &#34;mapbox&#34; &gt;}} &#34;mapbox使用介绍&#34;) 中介绍。  


#### mermaid 流程图工具
mermaid shortcode 使用 Mermaid 库提供绘制图表和流程图的功能。  

这部分内容在 [mermaid]({{&lt; ref &#34;mermaid&#34; &gt;}} &#34;mermaid使用介绍&#34;) 中介绍。  

### 数学公式
可以在 [latexlive](https://www.latexlive.com/) 预览编辑  
```tex
$c = \sqrt{10^{\frac{dBm}{10}} \cdot Z \cdot 10^{-3}} \cdot  10^6$
```
显示效果如下：

$c = \sqrt{10^{\frac{dBm}{10}} \cdot Z \cdot 10^{-3}} \cdot  10^6$  





---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/%E6%96%87%E6%A1%A3%E6%95%99%E7%A8%8B/  

