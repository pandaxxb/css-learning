# 盒模型

> css中，一切元素都是盒子，理解css盒模型的原理是学习css的重中之重。

### 盒模型的各个部分

一个完整的盒模型由四个部分组成。

- Content box：用来显示内容的区域，大小可以通过设置 `width` 和 `height`。
- Padding box：包围在内容区域外部的空白区域，大小通过`padding`相关属性设置。
- Border box：边框盒包裹在内容和内边距之外，大小及样式由`border`相关属性设置。
- Margin box：盒模型最外面的区域，是盒子和其他盒子之间的空白区域,大小通过`margin`相关属性设置。

几点补充：

1. `background`相关属性设置的内容展示在Padding box和Content box之中；
2. 滚动条占据的是Padding box的空间；
3. `outline`和`box-shadow`占据的是Margin box的空间；

[一个简单的demo](https://codepen.io/pandaxxb/pen/eYvLRQv)

### 块级盒子（Block box）和内联盒子(Inline box)

块级盒子的特性：

- 盒子会在内联的方向上扩展并占据父容器在该方向上的所有可用空间，在绝大数情况下意味着盒子会和父容器一样宽
- 每个盒子都会换行
- `width`和`height`属性可以发挥作用
- `padding`、`margin`、`border`会将其他元素从当前盒子周围“推开”

内联盒子的特性：

- 盒子不会产生换行
- `width`和`height`属性将不起作用，盒子的宽高取决于盒子内部内容的大小
- 垂直方向的`padding`、`margin`、`border`会被应用但是不会把其他盒子推开
- 水平方向的`padding`、`margin`、`border`会被应用且会把其他处于`inline`状态的盒子推开

通过设置元素的`display`属性值，决定盒子的外部显示类型。

[一个简单的demo](https://codepen.io/pandaxxb/pen/GRWXvQp)

### box-sizing属性

​	box-sizing属性值决定了盒模型如何计算盒子的大小。默认情况下，页面上的所有元素的box-sizing属性值均为content-box（IE浏览器除外）。

​	`box-sizing: content-box`称为标准盒模型。在标准模型中，`width`和`height`属性决定的是Content box的宽高，整个盒子的大小还需要加上`padding`和`border`。需要注意的是，`margin`虽然会影响盒子在页面所占空间，但是它影响的是盒子外部空间，盒子的大小及可视范围都是到边框位置，因此`margin`不计入盒子的大小。

​	`box-sizing: border-box`称为替代（IE）盒模型。在替代模型中，`width`和`height`属性决定的就是Border box的宽高 ，即可见宽高。而此时content box的宽高就等于`width`和`height`减去`padding`和`border`得到。

