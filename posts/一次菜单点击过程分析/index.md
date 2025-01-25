# 一次菜单点击过程分析


基于代码分析，一次菜单点击的调用流程如下：  
&lt;!--more--&gt;

{{&lt; mermaid &gt;}}
graph LR
    A[硬件层] --&gt; |中断| B[驱动层]
    B --&gt; |事件| C[处理层]
    C --&gt; |命令| D[显示层]
    
    subgraph 硬件层
        A1[GT911触摸屏]
        A2[RA8875 LCD]
    end
    
    subgraph 驱动层
        B1[触摸驱动]
        B2[显示驱动]
        B3[I2C驱动]
    end
    
    subgraph 处理层
        C1[触摸处理]
        C2[菜单处理]
        C3[事件分发]
    end
    
    subgraph 显示层
        D1[菜单渲染]
        D2[UI更新]
        D3[硬件加速]
    end
{{&lt; /mermaid &gt;}}

---

> 作者: ohmytime  
> URL: http://localhost:1313/posts/%E4%B8%80%E6%AC%A1%E8%8F%9C%E5%8D%95%E7%82%B9%E5%87%BB%E8%BF%87%E7%A8%8B%E5%88%86%E6%9E%90/  

