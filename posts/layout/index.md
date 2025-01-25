# 布局Layout


1. 高度可配置：支持多种分辨率和主题  
2. 维护性好：布局参数集中管理  
3. 扩展性强：易于添加新的布局主题  
4. 编译时优化：使用常量表达式提高性能  
5. 结构清晰：布局参数分类组织  

&lt;!--more--&gt;

### Layout 布局框架图

{{&lt; mermaid &gt;}}

graph LR
    A[screen_layout.h] --&gt; B1[160x128布局]
    A --&gt; B2[320x240布局]
    A --&gt; B3[480x320布局]
    A --&gt; B4[800x480布局]

    subgraph 布局定义
        C1[按钮布局]
        C2[频率显示布局]
        C3[状态栏布局]
        C4[菜单布局]
        C5[FFT显示布局]
    end

    subgraph 主题系统
        D1[颜色主题]
        D2[字体配置]
        D3[间距配置]
        D4[组件尺寸]
    end

    B1 --&gt; C1
    B1 --&gt; C2
    B1 --&gt; C3
    B2 --&gt; C1
    B2 --&gt; C2
    B2 --&gt; C3
    B3 --&gt; C1
    B3 --&gt; C2
    B3 --&gt; C3
    B4 --&gt; C1
    B4 --&gt; C2
    B4 --&gt; C3

    C1 --&gt; D1
    C1 --&gt; D2
    C1 --&gt; D3
    C1 --&gt; D4

{{&lt; /mermaid &gt;}}

{{&lt; mermaid &gt;}}
graph LR
    A[LCD界面结构] --&gt; B[顶部区域]
    A --&gt; C[中部区域]
    A --&gt; D[底部区域]
    A --&gt; E[弹出窗口]

    subgraph 顶部区域
        B --&gt; B1[状态栏]
        B1 --- B11[时钟]
        B1 --- B12[WiFi状态]
        B1 --- B13[SD卡状态]
        
        B --&gt; B2[功能按钮]
        B2 --- B21[PRE/ATT]
        B2 --- B22[AGC/NB]
        B2 --- B23[模式选择]
    end

    subgraph 中部区域
        C --&gt; C1[频率显示]
        C1 --- C11[VFO-A]
        C1 --- C12[VFO-B]
        
        C --&gt; C2[频谱显示]
        C2 --- C21[FFT频谱]
        C2 --- C22[瀑布图]
        
        C --&gt; C3[状态指示]
        C3 --- C31[S表]
        C3 --- C32[功率/SWR]
    end

    subgraph 底部区域
        D --&gt; D1[功能按钮]
        D1 --- D11[频率步进]
        D1 --- D12[功能切换]
        D1 --- D13[菜单访问]
    end

    subgraph 弹出窗口
        E --&gt; E1[系统菜单]
        E --&gt; E2[键盘输入]
        E --&gt; E3[提示信息]
        E --&gt; E4[错误警告]
    end
{{&lt; /mermaid &gt;}}
### 布局结构定义
```c
// screen_layout.h
typedef const struct {
    // 顶部按钮布局
    const uint16_t TOPBUTTONS_X1;
    const uint16_t TOPBUTTONS_Y1;
    const uint16_t TOPBUTTONS_WIDTH;
    const uint16_t TOPBUTTONS_HEIGHT;
    
    // 频率显示区域
    const uint16_t FREQ_X_OFFSET_100;
    const uint16_t FREQ_Y_BASELINE;
    const uint16_t FREQ_HEIGHT;
    
    // 状态显示区域
    const uint16_t STATUS_BAR_X_OFFSET;
    const uint16_t STATUS_BAR_HEIGHT;
    
    // FFT和瀑布图区域
    const uint16_t FFT_HEIGHT_STYLE1;
    const uint16_t WTF_HEIGHT_STYLE1;
    
    // 字体配置
    const GFXfont *FREQ_FONT;
    const GFXfont *STATUS_TXRX_FONT;
} STRUCT_LAYOUT_THEME;
```

### 分辨率适配
```c
// screen_layout_800x480.cpp
extern &#34;C&#34; constexpr STRUCT_LAYOUT_THEME LAYOUT_THEMES[LAYOUT_THEMES_COUNT] = {
    // Default theme
    {
        .TOPBUTTONS_X1 = 0,
        .TOPBUTTONS_X2 = (LCD_WIDTH - 1),
        .TOPBUTTONS_Y1 = 95,
        .TOPBUTTONS_COUNT = 11,
        .TOPBUTTONS_WIDTH = (float32_t)((float32_t)LCD_WIDTH / 11),
        .TOPBUTTONS_HEIGHT = 50,
        
        .FREQ_HEIGHT = 51,
        .FREQ_WIDTH = 370,
        .FREQ_FONT = &amp;FreeSans36pt7b,
        
        // ... 其他布局参数
    },
    // 其他主题
};
```

### 布局使用
```c
// lcd.c
STRUCT_LAYOUT_THEME *LAYOUT = &amp;LAYOUT_THEMES[TRX.LayoutThemeId];

void LCD_displayTopButtons(bool redraw) {
    uint16_t x = LAYOUT-&gt;TOPBUTTONS_X1;
    uint16_t y = LAYOUT-&gt;TOPBUTTONS_Y1;
    uint16_t width = LAYOUT-&gt;TOPBUTTONS_WIDTH;
    uint16_t height = LAYOUT-&gt;TOPBUTTONS_HEIGHT;
    
    // 使用布局参数绘制按钮
    printButton(x, y, width, height, ...);
}
```
### 布局计算
```c
// 相对位置计算
.FREQ_Y_BASELINE = (uint16_t)(LAYOUT_THEMES[0].FREQ_Y_TOP &#43; 
                             LAYOUT_THEMES[0].FREQ_HEIGHT &#43; 
                             LAYOUT_THEMES[0].FREQ_TOP_OFFSET),

// 自适应宽度
.TOPBUTTONS_WIDTH = (float32_t)((float32_t)LCD_WIDTH / 
                               (float32_t)LAYOUT_THEMES[0].TOPBUTTONS_COUNT),
```
### 主题切换
```c
void LCD_Init(void) {
    // 选择布局主题
    LAYOUT = &amp;LAYOUT_THEMES[TRX.LayoutThemeId];
    
    // 选择颜色主题
    COLOR = &amp;COLOR_THEMES[TRX.ColorThemeId];
    
    // 应用布局
    LCD_redraw(true);
}
```
### 布局验证
```c
#if (LCD_WIDTH == 800 &amp;&amp; LCD_HEIGHT == 480)
    #define LAYOUT_THEMES_COUNT 8
    #define MAX_FFT_HEIGHT 275
    #define MAX_WTF_HEIGHT 195
#endif
```

### 布局特色

1. 常量布局：使用constexpr确保编译时计算  
2. 主题化：支持多个布局主题  
3. 分辨率适配：不同分辨率使用不同布局文件  
4. 相对定位：使用相对位置计算避免硬编码  
5. 模块化：按功能区域划分布局参数  

---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/layout/  

