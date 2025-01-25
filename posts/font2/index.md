# 一次点击的代码分析过程


### 字体引用框架图

{{&lt; mermaid &gt;}}

graph LR
    A[FreeSans字体系统] --&gt; B[频率显示字体]
    A --&gt; C[界面字体]
    A --&gt; D[状态字体]
    A --&gt; E[提示字体]

    B --&gt; B1[FreeSans36pt7b]
    B1 --- B11[主频率显示]
    B1 --- B12[VFO-A/B频率]
    B1 --- B13[频率输入]

    C --&gt; C1[FreeSans9pt7b]
    C1 --- C11[顶部按钮&lt;br&gt;PRE/ATT/AGC/模式选择]
    C1 --- C12[系统菜单&lt;br&gt;标题/选项/设置]
    C1 --- C13[底部按钮&lt;br&gt;步进/功能/快捷键]

    D --&gt; D1[FreeSans7pt7b]
    D1 --- D11[S表&lt;br&gt;信号强度/刻度]
    D1 --- D12[发射信息&lt;br&gt;功率/SWR/ALC]
    D1 --- D13[状态栏&lt;br&gt;时钟/温度/电压]

    E --&gt; E1[FreeSans12pt7b]
    E1 --- E11[工具提示&lt;br&gt;按钮/功能说明]
    E1 --- E12[系统信息&lt;br&gt;错误/警告/提醒]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef freq fill:#bbf,stroke:#333,stroke-width:2px;
    classDef ui fill:#bfb,stroke:#333,stroke-width:2px;
    classDef status fill:#fbf,stroke:#333,stroke-width:2px;
    classDef tooltip fill:#ffb,stroke:#333,stroke-width:2px;
    
    class B1 freq;
    class C1 ui;
    class D1 status;
    class E1 tooltip;

{{&lt; /mermaid &gt;}}




---

> 作者: ohmytime  
> URL: http://localhost:1313/posts/font2/  

