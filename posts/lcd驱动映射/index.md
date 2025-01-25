# LCD驱动映射



### LCD驱动映射的具体实现

```c
// lcd_driver.h
typedef struct {
    // 基础操作函数指针
    void (*init)(void);
    void (*reset)(void);
    void (*writeCmd)(uint8_t cmd);
    void (*writeData)(uint8_t data);
    uint8_t (*readData)(void);
    
    // 显示控制函数指针
    void (*setRotation)(uint8_t r);
    void (*setWindow)(uint16_t x1, uint16_t y1, uint16_t x2, uint16_t y2);
    void (*setBrightness)(uint8_t percent);
    
    // 绘图函数指针
    void (*drawPixel)(uint16_t x, uint16_t y, uint16_t color);
    void (*fillRect)(uint16_t x, uint16_t y, uint16_t w, uint16_t h, uint16_t color);
    void (*drawBitmap)(uint16_t x, uint16_t y, const uint8_t *bitmap, uint16_t w, uint16_t h);
    
    // RA8875特有功能函数指针
    void (*bte_copyArea)(uint16_t sx, uint16_t sy, uint16_t dx, uint16_t dy, 
                        uint16_t w, uint16_t h, bool fromEnd);
} LCD_Driver_Ops;

// RA8875驱动实现
static const LCD_Driver_Ops ra8875_ops = {
    .init = RA8875_Init,
    .reset = RA8875_Reset,
    .writeCmd = RA8875_WriteCmd,
    .writeData = RA8875_WriteData,
    .readData = RA8875_ReadData,
    .setRotation = RA8875_SetRotation,
    .setWindow = RA8875_SetWindow,
    .setBrightness = RA8875_SetBrightness,
    .drawPixel = RA8875_DrawPixel,
    .fillRect = RA8875_FillRect,
    .drawBitmap = RA8875_DrawBitmap,
    .bte_copyArea = RA8875_BTE_CopyArea
};

&lt;!--more--&gt;

// 全局驱动操作指针
static LCD_Driver_Ops *current_lcd_ops = NULL;

// 驱动初始化
void LCD_Driver_Init(void) {
    // 根据硬件配置选择驱动
#if defined(LCD_RA8875)
    current_lcd_ops = &amp;ra8875_ops;
#elif defined(LCD_ILI9341)
    current_lcd_ops = &amp;ili9341_ops;
#elif defined(LCD_ST7789)
    current_lcd_ops = &amp;st7789_ops;
#endif

// 调用具体驱动的初始化
    if(current_lcd_ops &amp;&amp; current_lcd_ops-&gt;init) {
        current_lcd_ops-&gt;init();
    }
}

// 统一的接口函数
void LCD_WriteCmd(uint8_t cmd) {
    if(current_lcd_ops &amp;&amp; current_lcd_ops-&gt;writeCmd) {
        current_lcd_ops-&gt;writeCmd(cmd);
    }
}

void LCD_DrawPixel(uint16_t x, uint16_t y, uint16_t color) {
    if(current_lcd_ops &amp;&amp; current_lcd_ops-&gt;drawPixel) {
        current_lcd_ops-&gt;drawPixel(x, y, color);
    }
}
```

### 映射过程：

#### 1. 编译时选择:
```c
#if defined(LCD_RA8875)
    current_lcd_ops = &amp;ra8875_ops;
#endif
```
#### 2. 函数调用映射:
```c
// 调用示例
void LCD_DrawPixel(uint16_t x, uint16_t y, uint16_t color) {
    // current_lcd_ops-&gt;drawPixel 实际指向 RA8875_DrawPixel
    current_lcd_ops-&gt;drawPixel(x, y, color);
}
```
#### 3. 具体实现:
```c
// RA8875具体实现
static void RA8875_DrawPixel(uint16_t x, uint16_t y, uint16_t color) {
    RA8875_SetCursor(x, y);
    RA8875_WriteReg(0x02, color &gt;&gt; 8);    // 颜色高字节
    RA8875_WriteReg(0x03, color &amp; 0xFF);  // 颜色低字节
}
```

  
这种设计的优点:  
零额外开销：函数指针在编译时确定  
类型安全：结构体定义保证函数签名匹配  
接口统一：上层代码使用统一接口  
易于扩展：添加新驱动只需实现ops结构体  
功能灵活：可以根据硬件特性添加专有功能  


---

> 作者: [ohmytime](ohmytime.github.io)  
> URL: https://ohmytime.github.io/posts/lcd%E9%A9%B1%E5%8A%A8%E6%98%A0%E5%B0%84/  

