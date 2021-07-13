# 值与单位

> CSS中使用的每个属性都允许拥有一个或一组值。

### 数值

- 数字——1、0.4

- 百分比——50%

- 长度——10px、30em

  - 绝对长度单位——与任何其他东西没有关系，通常总是相同的大小

    | 单位 | 名称         | 等价换算            |
    | ---- | ------------ | ------------------- |
    | cm   | 厘米         | 1cm = 96px/2.54     |
    | mm   | 毫米         | 1mm = 1/10th of 1cm |
    | Q    | 四分之一毫米 | 1Q = 1/40th of 1cm  |
    | in   | 英寸         | 1in = 2.54cm = 96px |
    | pc   | 十二点活字   | 1pc = 1/16th of 1in |
    | pt   | 点           | 1pt = 1/72th of 1in |
    | px   | 像素         | 1px = 1/96th of 1in |

  - 相对长度单位——相对一些其他东西计算具体大小

    | 单位 | 相对于                                                       |
    | ---- | ------------------------------------------------------------ |
    | em   | 在font-size中相对于父元素字体大小，在其他属性中相对于自身字体大小 |
    | ex   | 字符‘x’的高度;对于很多字体来说，`1ex ≈ 0.5em`                |
    | ch   | 数字’0‘的宽度;如果无法确定“ 0”字形的大小，则必须假定其宽为 `0.5em`，高为 `1em` |
    | cap  | 元素字体 font 的“上限高度”（cap height，大写字母的标称高度（nominal height）） |
    | ic   | 在用于渲染的字体中找到的“水”字形的使用预先测量(简单说就是宽度) |
    | rem  | 根元素的字体大小                                             |
    | lh   | 元素的line-height                                            |
    | rlh  | 根元素的line-height                                          |
    | vw   | 视窗宽度的1%                                                 |
    | vh   | 视窗高度的1%                                                 |
    | vi   | 初始包含块大小的 1%，在根元素的行内轴方向上                  |
    | vd   | 初始包含块大小的 1%，在根元素的区块轴方向上                  |
    | vmin | 视窗较小尺寸的1%                                             |
    | vmax | 视窗较大尺寸的1%                                             |

### 颜色

- [颜色关键字](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value#%E9%A2%9C%E8%89%B2%E5%85%B3%E9%94%AE%E5%AD%97)
- transparent关键字——完全透明，等同于rgba(0, 0, 0, 0);
- currentColor关键字——当前元素color属性值
- RGB颜色——`#RRGGBB[AA]`、`rgb[a](R, G, B[, A])`、 `rgb[a](R G B[ / A])`
- HSL颜色——色相-饱和度-亮度，`hsl[a](H, S, L[, A])`、`hsl[a](H S L[ / A])`
- 系统颜色

### 图片

- 一个图像被引用为CSS [`url`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/url())数据类型使用url()方法
- 一个CSS[`gradient`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/gradient)
- 页面的一个部分，定义在[element()][https://developer.mozilla.org/zh-CN/docs/Web/CSS/element()]方法中

### 位置

- 位置关键字——top|bottom|right|left|center
- 长度
- 百分比

