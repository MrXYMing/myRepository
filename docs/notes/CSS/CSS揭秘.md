### CSS揭秘

### 一、CSS编码技巧
#### 尽量减少改动时要编辑的地方
#### 1. em rem
- em:相对长度单位，相对于当前对象内文本的字体尺寸；
- rem：css3新增的相对但对，只相对于html跟元素。

#### 2. [例子](../../demo/CSS_SECRETS/index.html#n1-2)
初始样式设计：
```
.n1-2-start{
    padding:6px 16px;
    border:1px solid #446d88;
    background: #58a linear-gradient(#77a0bb,#58a);
    border-radius: 4px;
    box-shadow:0 1px 5px gray;
    color:white;
    text-shadow:0 -1px 1px #335166;
    font-size: 20px;
    line-height: 30px;
}
```

问题：
1. 改变字号时，要同时调整行高；为使按钮看起来协调，可能还需要调整padding，shadow等。这样的话，需要修改的地方太多且杂，不易维护。
2. 需要改变主题颜色时，可能需要覆盖四条声明（border-color、background、box-shadow和text-shadow）。问题同上。

解决：
1. 当某些值相互依赖时，应该把他们的相互关系用代码表达出来；同时需要审视到底哪些效果应该跟着按钮一起放大，而哪些效果是保持不变的。
```
.n1-2-size{
    padding:.3em .8em;
    border:1px solid #446d88;
    background: #58a linear-gradient(#77a0bb,#58a);
    border-radius: .2em;
    box-shadow:0 .05em .25em gray;
    color:white;
    text-shadow:0 -.05em .05em #335166;
    font-size: 125%;
    line-height: 1.5;
}
```
*ps：当希望字号和腹肌的字号建立关联，可以采用em单位；如果希望和根级字号（<html>元素的字号）相关联，用em的话会导致复杂的计算，可以使用rem单位，*
2. 只要把半透明的黑色或白色叠加到主色调上，即可产生主色调的亮色和暗色变体。
```
.n1-2-color{
    padding:.3em .8em;
    border:1px solid rgba(0,0,0,.1);
    background: #58a linear-gradient(hsla(0,0%,100%,.2),transparent);
    border-radius: .2em;
    box-shadow:0 .05em .25em rgba(0,0,0,.5);
    color:white;
    text-shadow:0 -.05em .05em rgba(0,0,0,.5);
    font-size: 125%;
    line-height: 1.5;
}

.n1-2-color.cancel{
    background-color: #c00;
}
.n1-2-color.ok{
    background-color: #6b0;
}
```

---

### 第二章 背景与边框

#### 1.半透明边框

- 半透明颜色:rgba(),hsla();

    1. [grba(R,G,B,A)](http://www.css88.com/book/css/values/color/rgba.htm):
        - R：红色值。正整数 | 百分数
        - G：绿色值。正整数 | 百分数
        - B：蓝色值。正整数 | 百分数
        - A：Alpha透明度。取值0~1之间。
    2. [hsla](H,S,L,A)(http://www.css88.com/book/css/values/color/hsla.htm)
        - H：Hue(色调)。0(或360)表示红色，120表示绿色，240表示蓝色，也可取其他数值来指定颜色。取值为：0 - 360
        - S：Saturation(饱和度)。取值为：0.0% - 100.0%
        - L：Lightness(亮度)。取值为：0.0% - 100.0%
        - A：Alpha透明度。取值0~1之间。

- [background-clip:padding-box;](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)

    1. border-box: 背景延伸到边框外沿（但是在边框之下）;
    2. padding-box: 边框下面没有背景，即背景延伸到内边距外沿;
    3. content-box: 背景裁剪到内容区 (content-box) 外沿;
    4. text: 背景被裁剪为文字的前景色。

    *注意：兼容到ie9+，不继承属性*