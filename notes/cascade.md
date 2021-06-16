# Cascade

> 层叠是CSS的一个基本特征，它是一个定义了如何合并来自多个源的属性值的算法。它在CSS处于核心地位，CSS的全称层叠样式表正是强调了这一点。

层叠主要基于以下三个因素来定义多条CSS规则产生冲突时如何应用规则，根据重要性排序，前面的最重要。

1. 重要程度
2. 优先级
3. 资源的顺序

## 资源的顺序

​	CSS规则出现的位置及顺序是层叠算法在实现冲突解决方案时需要考虑的第一个因素。针对具有相同优先级选择器的多条CSS规则，最后声明的一条规则将在冲突中胜出，不管该条规则是通过<link>标签引入的或者是在<style>元素中声明的。

​	上述规则同样适用于同一条CSS规则中出现的多条针对同一属性的声明，在这种情况下，最后一条声明的值将会被应用到该属性上。利用这个规则可以方便地实现对于不支持某些特殊值的浏览器的备选方案。

```css
/*
** 对于不支持clamp函数的浏览器，第一条font-size声明将会得到应用；而对于支持clamp函数的浏览器，第一条声明将会被废弃，而第二条声明会得到应用
*/
.my-element{
    font-size: 1.5rem;
    font-size: clamp(1.5rem, calc(1rem + 3vw), 2rem);
}
```

### 优先级

​	优先级是一种通过计算权重和分数来决定哪个CSS选择器更优先的算法。具有更高优先级的CSS规则即使声明在较为前面的位置，它最终也能战胜之后声明的CSS规则并最终得到应用。

​	每一种选择器都有自己的优先级分数，一个选择器的优先级由四个部分相加，可以近似认为是一个四位数，每一位上的得分规则如下：

1. 千位：声明在内联样式的属性则该位得一分。此类声明没有选择器，因此它得分总是1000。
2. 百位：选择器中包含ID选择器则该位得一分。
3. 十位：选择器中包含类选择器、属性选择器或者伪类选择器则该位得一分。
4. 个位：选择器中包含元素选择器、伪元素选择器则该位得一分。

***注：通用选择器、组合符（+,>,~, ' '）、和否定（:not）伪类不影响优先级。***

***注：各位置计算时不允许进位，即无论多少个类选择器得权重叠加，都不会超过一个ID选择器的权重。***

***注：复合选择器的优先级计算是累加的，并不是取最高位。例：#id.class的优先级为百位得一分，十位得一分。***

| 选择器                                  | 千位 | 百位 | 十位 | 个位 | 优先级 |
| --------------------------------------- | ---- | ---- | ---- | ---- | ------ |
| h1                                      | 0    | 0    | 0    | 1    | 0001   |
| h1:not(.class)                          | 0    | 0    | 1    | 1    | 0011   |
| h1 + p::first-letter                    | 0    | 0    | 0    | 3    | 0003   |
| li > a[href*="en-US"] > .inline-warning | 0    | 0    | 2    | 2    | 0022   |
| #id                                     | 0    | 1    | 0    | 0    | 0100   |
| 内联样式                                | 1    | 0    | 0    | 0    | 1000   |

!important是一个特殊的CSS，它拥有超过上述所有选择器计算所得的优先级，可以简单的理解成它的优先级为10000。

***注：覆盖 `!important` 唯一的办法就是另一个 `!important` 具有 相同优先级 而且顺序靠后，或者更高优先级。***

### 重要程度

​	在理解重要程度如何影响层叠算法之前，需要先理解一下源（origin）和重要性的概念；

​	CSS的源包括以下三种：

1. 用户代理样式——浏览器给任何网页设置的默认样式，不同浏览器可能有不同的默认样式，导致了开发者通常使用CSS reset样式表来重写一些属性。
2. 用户样式——来源于当前网页用户所使用的操作系统决定的一些特性，例如字体大小，或是关闭动画。也可能来源于一些允许用户编写自定义CSS规则的浏览器插件。
3. 开发者样式——当前网页开发者编写的CSS规则。

   一条CSS中的声明分为以下四种重要性，按照重要性由低到高排序：

1. 普通声明，例如font-size,background,color
2. animation声明
3. !important声明
4. transitions声明

   理解了源和重要性的概念之后，就可以理解层叠顺序的生成逻辑——首先过滤来自不同源的全部规则，并保留要应用到指定元素上的那些规则；其次，根据重要性以及源对规则进行重要程度排序，最终重要程度排序结果如下（越往后的越重要）:

1. 用户代理的普通声明
2. 用户的普通声明
3. 页面作者的普通声明
4. animation声明
5. 页面作者的!important声明
6. 用户的!important声明
7. 用户代理的!important声明
8. transitions声明

**理解了重要程度、优先级、资源顺序三个概念之后，可以给出CSS层叠如解决不同规则之间产生冲突时并应用哪一条具体规则的结论：**

1. **应用重要程度高的规则**
2. **如果重要程度一样，则应用优先级高的规则**
3. **如果优先级一样，则应用最后声明的规则**
