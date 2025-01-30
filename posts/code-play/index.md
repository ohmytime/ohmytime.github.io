# Code Play


### 高级代码块用法 code fences

&lt;!--more--&gt;

#### 自定义一些属性

- 自定义开始行号  
- 自定义高亮行


````markdown {.no-header}
```go {.myclass linenos=table,hl_lines=[8,&amp;#34;15-17&amp;#34;],linenostart=199}
// ... code
```
````
上面的代码块渲染的效果如下：  
```go {.myclass linenos=table,hl_lines=[8,&#34;15-17&#34;],linenostart=100}
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
printf(&#34;test&#34;);
```

#### 添加代码块标题

````markdown
```js {title= &#34;test.js&#34;}
console.log(&#39;hello FixIt!&#39;;);
```
````
给代码块添加标题，渲染效果如下：  
```js {title=&#34;标题是test.js&#34;}
console.log(&#39;hello FixIt!&#39;);
```

#### 隐藏头部信息

````md
```js {.no-header}
function forEach(elements, handler) {
  elements = elements || [];
  for (let i = 0; i &lt; elements.length; i&#43;&#43;) {
    handler(elements[i]);
  }
}
```
````

渲染效果如下：  

```js {.no-header}
function forEach(elements, handler) {
  elements = elements || [];
  for (let i = 0; i &lt; elements.length; i&#43;&#43;) {
    handler(elements[i]);
  }
}
```

&lt;!-- 带有 CSS 类的分割线 --&gt;
{.awesome-hr}

---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/code-play/  

