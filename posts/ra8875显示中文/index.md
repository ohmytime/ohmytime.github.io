# RA8875显示中文


### RA8875内置了GT字库支持，可以直接显示中文。
    

#### 字库特性

GT21L16S2W / GT21L16T2W 字库支持:  
    1. GB2312: 6763个汉字  
    2. ASCII: 95个字符  
    3. 字体大小: 16x16, 24x24, 32x32  

[参考 → RA8875显示小字库](https://www.armbbs.cn/forum.php?mod=viewthread&amp;tid=105680)

{{&lt; mermaid &gt;}}
graph TB
    A[RA8875中文显示] --&gt; B[字库配置]
    A --&gt; C[显示函数]
    A --&gt; D[字符集]
    
    B --&gt; B1[内置GT字库]
    B --&gt; B2[外置字库]
    
    C --&gt; C1[文本模式]
    C --&gt; C2[图形模式]
    
    D --&gt; D1[GB2312]
    D --&gt; D2[BIG5]
{{&lt; /mermaid &gt;}}


#### 1. RA8875字库初始化
```c
// RA8875字库初始化
void RA8875_FontInit(void) {
    // 选择内部CGROM
    RA8875_WriteReg(0x21, 0x00);
    
    // 设置字体编码方式为GB2312
    RA8875_WriteReg(0x22, 0x00);
    
    // 设置文本模式
    RA8875_WriteReg(0x40, 0x00);
}
```

#### 2. 文本显示函数
``` c
// 显示中文字符串
void RA8875_ShowChinese(uint16_t x, uint16_t y, const char *str) {
    // 设置文本写入位置
    RA8875_SetTextCursor(x, y);
    
    // 设置文本颜色
    RA8875_SetTextColor(FG_COLOR);
    
    // 发送字符串
    while(*str) {
        RA8875_WriteData(*str&#43;&#43;);
    }
}

// 设置字体大小
void RA8875_SetFontSize(uint8_t size) {
    // size: 0=16x16, 1=24x24, 2=32x32
    uint8_t cmd = 0x02;  // 默认16x16
    switch(size) {
        case 1: cmd = 0x03; break;  // 24x24
        case 2: cmd = 0x04; break;  // 32x32
    }
    RA8875_WriteReg(0x22, cmd);
}
```

#### 4. 使用示例
```c
void LCD_ShowChineseMenu(void) {
    RA8875_FontConfig config = {
        .size = 1,           // 24x24大小
        .spacing = 0,        // 默认间距
        .encoding = 0,       // GB2312编码
        .color = COLOR_WHITE,
        .bgColor = COLOR_BLACK
    };
    
    // 配置字体
    RA8875_ConfigFont(&amp;config);
    
    // 显示菜单项
    RA8875_ShowChinese(10, 10, &#34;系统设置&#34;);
    RA8875_ShowChinese(10, 40, &#34;频率设置&#34;);
    RA8875_ShowChinese(10, 70, &#34;显示设置&#34;);
}
```
#### 5. 性能优化
```c
// 使用DMA加速显示
void RA8875_ShowChineseDMA(uint16_t x, uint16_t y, const char *str, uint16_t len) {
    // 设置文本位置
    RA8875_SetTextCursor(x, y);
    
    // 启动DMA传输
    HAL_DMA_Start_IT(&amp;hdma_memtomem,
        (uint32_t)str,
        RA8875_DATA_ADDR,
        len
    );
}
```

---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/ra8875%E6%98%BE%E7%A4%BA%E4%B8%AD%E6%96%87/  

