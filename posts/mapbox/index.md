# 扩展 Shortcode - Mapbox


{{&lt; version 0.2.0 &gt;}}

`mapbox` shortcode 使用 [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js) 库提供互动式地图的功能。

&lt;!--more--&gt;

[Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js) 是一个 JavaScript 库，它使用 WebGL, 以 [vector tiles](https://docs.mapbox.com/help/glossary/vector-tiles/) 和 [Mapbox styles](https://docs.mapbox.com/mapbox-gl-js/style-spec/) 为来源，将它们渲染成互动式地图。

`mapbox` shortcode 有以下命名参数来使用 Mapbox GL JS:

* **lng** *[必需]*（**第一个**位置参数）

    地图初始中心点的经度，以度为单位。

* **lat** *[必需]*（**第二个**位置参数）

    地图初始中心点的纬度，以度为单位。

* **zoom** *[可选]*（**第三个**位置参数）

    地图的初始缩放级别，默认值是 `10`。

* **marked** *[可选]*（**第四个**位置参数）

    是否在地图的初始中心点添加图钉，默认值是 `true`。

* **light-style** *[可选]*（**第五个**位置参数）

    浅色主题的地图样式，默认值是 [前置参数](../theme-documentation-content#front-matter) 或者 [网站配置](../theme-documentation-basics#site-configuration) 中设置的值。

* **dark-style** *[可选]*（**第六个**位置参数）

    深色主题的地图样式，默认值是 [前置参数](../theme-documentation-content#front-matter) 或者 [网站配置](../theme-documentation-basics#site-configuration) 中设置的值。

* **navigation** *[可选]*

    是否添加 [NavigationControl](https://docs.mapbox.com/mapbox-gl-js/api#navigationcontrol), 默认值是 [前置参数](../theme-documentation-content#front-matter) 或者 [网站配置](../theme-documentation-basics#site-configuration) 中设置的值。

* **geolocate** *[可选]*

    是否添加 [GeolocateControl](https://docs.mapbox.com/mapbox-gl-js/api#geolocatecontrol), 默认值是 [前置参数](../theme-documentation-content#front-matter) 或者 [网站配置](../theme-documentation-basics#site-configuration) 中设置的值。

* **scale** *[可选]*

    是否添加 [ScaleControl](https://docs.mapbox.com/mapbox-gl-js/api#scalecontrol), 默认值是 [前置参数](../theme-documentation-content#front-matter) 或者 [网站配置](../theme-documentation-basics#site-configuration) 中设置的值。

* **fullscreen** *[可选]*

   是否添加 [FullscreenControl](https://docs.mapbox.com/mapbox-gl-js/api#fullscreencontrol), 默认值是 [前置参数](../theme-documentation-content#front-matter) 或者 [网站配置](../theme-documentation-basics#site-configuration) 中设置的值。

* **width** *[可选]*

    地图的宽度，默认值是 `100%`。

* **height** *[可选]*

    地图的高度，默认值是 `20rem`。

一个简单的 `mapbox` 示例：

```go-html-template
{{&lt;/* mapbox 113.953277 22.559102 11 */&gt;}}
或者
{{&lt;/* mapbox lng=113.953277 lat=22.559102 zoom=11 */&gt;}}
```

呈现的输出效果如下：

{{&lt; mapbox 113.953277 22.559102 11 &gt;}}

一个带有自定义样式的 `mapbox` 示例：

```go-html-template
{{&lt;/* mapbox -122.252 37.453 10 false &#34;mapbox://styles/mapbox/streets-zh-v1&#34; */&gt;}}
或者
{{&lt;/* mapbox lng=-122.252 lat=37.453 zoom=10 marked=false light-style=&#34;mapbox://styles/mapbox/streets-zh-v1&#34; */&gt;}}
```

呈现的输出效果如下：

{{&lt; mapbox -122.252 37.453 10 false &#34;mapbox://styles/mapbox/streets-zh-v1?optimize=true&#34; &gt;}}




---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/mapbox/  

