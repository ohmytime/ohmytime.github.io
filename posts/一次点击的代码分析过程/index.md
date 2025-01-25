# 一次点击的代码分析过程


### 字体引用框架图

{{&lt; mermaid &gt;}}

graph TD
    A[触摸中断] --&gt; B{GT911_Scan}
    B --&gt; |读取坐标| C[TOUCHPAD_processTouch]
    C --&gt; D{触摸类型判断}
    
    D --&gt;|单击| E[LCD_processTouch]
    D --&gt;|长按| F[LCD_processHoldTouch]
    D --&gt;|滑动| G[LCD_processSwipeTouch]
    
    E --&gt; H{菜单项判断}
    H --&gt;|有效| I[执行菜单回调]
    H --&gt;|无效| J[返回]
    
    I --&gt; K[更新菜单状态]
    K --&gt; L[请求重绘]
    L --&gt; M[RA8875硬件加速绘制]

{{&lt; /mermaid &gt;}}




---

> 作者: ohmytime  
> URL: http://localhost:1313/posts/%E4%B8%80%E6%AC%A1%E7%82%B9%E5%87%BB%E7%9A%84%E4%BB%A3%E7%A0%81%E5%88%86%E6%9E%90%E8%BF%87%E7%A8%8B/  

