# 选择器

> 在CSS中，选择器用来指定网页上我们想要样式化的元素。CSS选择器提供了很多种方法，因此，熟悉理解选择器的不同使用方式以及了解它们的工作原理，能够让我们更加精细的编写CSS样式表。

### CSS规则

​	一条CSS规则由**一个或多个选择器(Selector)**起头，接着是**一对大括号`{ }`**，在大括号内部定义一个或多个形式为**属性(property):值(value)**的**声明(declaration)**。

![An image of a CSS rule with the selector .my-css-rule](https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/hFR4OOwyH5zWc5XUIcyu.svg)

### 选择器的类型

- 通配选择器

  ```css
  /* 适配所有元素，伪元素除外 */
  * { }
  ```

  注：不建议使用通配选择器，因为它是[性能最低的选择器](https://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/)

- 类型选择器

  ```css
  h1 { }
  ```

- 类选择器

  ```css
  .box { }
  /* 与下面的属性选择器语句等价 */
  [class~='box'] { }
  ```

- ID选择器

  ```css
  /* 如果页面中存在一个以上id为unique的元素，所有元素都会应用这条css规则 */
  /* 出于建议同一页面中元素的id为唯一值以及样式规则的复用性，因此应该避免使用ID选择器 */
  #unique { }
  /* 与下面的属性选择器语句等价 */
  [id='unique'] { }
  ```

  注：当元素的类或ID以数字开头时，在使用CSS选择器时，需要将数字进行转义，否则选择器将无法正确匹配到对应元素。因此除非特殊需要，避免使用以数字开头的类或ID。

  > In CSS, identifiers (including element names, classes, and IDs in [selectors](https://www.w3.org/TR/CSS21/selector.html)) can contain only the characters [a-zA-Z0-9] and ISO 10646 characters U+00A0 and higher, plus the hyphen (-) and the underscore (_); they cannot start with a digit, two hyphens, or a hyphen followed by a digit. Identifiers can also contain escaped characters and any ISO 10646 character as a numeric code (see next item). For instance, the identifier "B&W?" may be written as "B\&W\?" or "B\26 W\3F".

  详细可以[点击此处](https://www.w3.org/TR/CSS21/syndata.html#characters)查看。

- 标签属性选择器

  ```css
  /* 适配所有带有title属性的元素 */
  [title] { }
  
  /* 适配所有带有href属性且属性值等于”https://example.com“的元素 */
  [href="https://example.com"] { }
  
  /* 适配所有带有href属性且属性值包含"example"的元素 */
  [href*="example"] { }
  
  /* 适配所有带有href属性且属性值以".org"结尾的元素 */
  [href$=".org"] { } 
  
  /* 适配所有带有href属性且属性值以"https"开头的元素 */
  [href^="https"] { }
  
  /* 适配所有带有class属性且属性值包含以空格分隔的"logo"的元素 */
  [class~="logo"] { }
  
  /* 适配所有带有alt属性且属性值等于"image"或以"image-"开头的元素 */
  [alt|="image"] { }
  
  /* 在属性选择器的右方括号前添加一个用空格隔开的字母 i（或 I），可以在匹配属性值时忽略大小写（支持 ASCII 字符范围之内的字母） */
  [attr operator value i] { }
  
  /* 在属性选择器的右方括号前添加一个用空格隔开的字母 s（或 S），可以在匹配属性值时区分大小写（支持 ASCII 字符范围之内的字母）。 */
  [attr operator value s] { }
  ```

  注：默认情况下选择器的值区分大小写。

- 伪类选择器

  ```css
  /* 适配所有用户指针悬停的元素 */
  :hover { }
  
  /* 在一个选择器中可以同时一起写多个伪类，下面这条规则适配所有用户指针悬停的非图片元素 */
  :not(img):hover { }
  ```

- 伪元素选择器

  ```css
  /* 一个选择器中只能使用一个伪元素 */
  /* 适配所有元素的第一行 */
  ::first-line { }
  ```

- 后代选择器

  ```css
  /* 匹配p元素中包含的所有后代span元素 */
  p span { }
  ```

- 子选择器

  ```css
  /* 匹配p元素中包含的所有直接后代span元素 */
  p > span { }
  ```

- 相邻兄弟选择器

  ```css
  /* 适配紧跟着img元素的p元素, p和img元素必须是属于同一个父元素的子元素 */
  img + p { }
  ```

- 通用兄弟选择器

  ```css
  /* 适配与p元素同级，且在P元素之后的所有span元素 */
  p ~ span { }
  ```

### 选择器列表

​	多个使用相同样式的CSS选择器可以混编为一个”选择器列表“。

```css
/* 适配所有h1元素或p元素 */
h1,
p { }
```

### 复合选择器

​	将不同的CSS选择器结合起来，形成一个”复合选择器“，用来增强选择器的精准性和可读性。

```css
/* 适配所有含有"my-calss"类的a元素 */
a.my-class { }
```

