---
title: 背景与边框
slug: Learn/CSS/Building_blocks/Backgrounds_and_borders
---
{{LearnSidebar}}{{PreviousMenuNext("Learn/CSS/Building_blocks/The_box_model", "Learn/CSS/Building_blocks/Handling_different_text_directions", "Learn/CSS/Building_blocks")}}

在这节课中，我们来看看，使用 CSS 背景和边框来做一些，具有一些创造性的事情。渐变、背景图像和圆角，背景和边框的巧妙运用是 CSS 中许多样式问题的答案。

<table class="learn-box standard-table">
  <tbody>
    <tr>
      <th scope="row">预备知识：</th>
      <td>
        基本的计算机知识，<a
          href="/zh-CN/docs/Learn/Getting_started_with_the_web/Installing_basic_software"
          >安装基本的软件</a
        >，<a
          href="/zh-CN/docs/Learn/Getting_started_with_the_web/Dealing_with_files"
          >文件处理</a
        >基本知识，HTML 基础知识 (如果不了解 HTML，请移步
        <a href="/zh-CN/docs/Learn/HTML/Introduction_to_HTML">学习 HTML 入门</a
        >)，以及 CSS 如何工作的基本常识 (如果不了解 CSS，请移步
        <a href="/zh-CN/docs/Learn/CSS/First_steps">学习 CSS 第一步</a>.)
      </td>
    </tr>
    <tr>
      <th scope="row">目标：</th>
      <td>学习如何在盒模型中使用背景和边框。</td>
    </tr>
  </tbody>
</table>

## CSS 的背景样式

CSS {{cssxref("background")}} 属性是我们将在本课中学习的许多普通背景属性的简写。如果您在样式表中发现了一个复杂的背景属性，可能会觉得难以理解，因为可以同时传入这么多值。

```css
.box {
  background: linear-gradient(105deg, rgba(255,255,255,.2) 39%, rgba(51,56,57,1) 96%) center center / 400px 200px no-repeat,
  url(big-star.png) center no-repeat, rebeccapurple;
}
```

在本教程的后面部分，我们将返回到简写的工作方式，但是首先，我们通过分开使用各个普通背景属性的方式，看一下在 CSS 中使用背景可以做哪些不同的事情。

### 背景颜色

{{cssxref("background-color")}} 属性定义了 CSS 中任何元素的背景颜色。属性接受任何有效的`<color>值`。背景色扩展到元素的内容和内边距的下面。

在下面的示例中，我们使用了各种颜色值来为元素盒子添加背景颜色：heading 和{{htmlelement("span")}}元素。

**尝试修改为任何可用的 [\<color>](/zh-CN/docs/Web/CSS/color_value) 值。**

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/color.html", '100%', 800)}}

### 背景图片

{{cssxref("background-image")}} 属性允许在元素的背景中显示图像。在下面的例子中，我们有两个方框——一个是比方框大的背景图像，另一个是星星的小图像。

这个例子演示了关于背景图像的两种情形。默认情况下，大图不会缩小以适应方框，因此我们只能看到它的一个小角，而小图则是平铺以填充方框。在这种情况下，实际的图像只是单独的一颗星星。

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/background-image.html", '100%', 800)}}

**如果除了背景图像外，还指定了背景颜色，则图像将显示在颜色的顶部。尝试向上面的示例添加一个 background-color 属性，看看效果如何。**

#### 控制背景平铺

{{cssxref("background-repeat")}} 属性用于控制图像的平铺行为。可用的值是：

- `no-repeat` — 不重复。
- `repeat-x` —水平重复。
- `repeat-y` —垂直重复。
- `repeat` — 在两个方向重复。

**在下面的示例中尝试这些值。我们已经将值设置为 no-repeat，因此您将只能看到一个星星。尝试不同的值—repeat-x 和 repeat-y—看看它们的效果如何。**

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/repeat.html", '100%', 800)}}

#### 调整背景图像的大小

在上面的例子中，我们有一个很大的图像，由于它比作为背景的元素大，所以最后被裁剪掉了。在这种情况下，我们可以使用 {{cssxref("background-size")}}属性，它可以设置长度或百分比值，来调整图像的大小以适应背景。

你也可以使用关键字：

- `cover` —浏览器将使图像足够大，使它完全覆盖了盒子区，同时仍然保持其高宽比。在这种情况下，有些图像可能会跳出盒子外
- `contain` — 浏览器将使图像的大小适合盒子内。在这种情况下，如果图像的长宽比与盒子的长宽比不同，则可能在图像的任何一边或顶部和底部出现间隙。

在下面的例子中，我使用了上面例子中的大图，并使用长度单位来调整方框内的大小。你可以看到这扭曲了图像。

试试下面：

- 改变用于修改背景大小的长度单位。
- 去掉长度单位，看看使用`background-size: cover` or `background-size: contain`会发生什么。
- 如果您的图像小于盒子，您可以更改 background-repeat 的值来重复图像。

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/size.html", '100%', 800)}}

#### 背景图像定位

{{cssxref("background-position")}} 属性允许您选择背景图像显示在其应用到的盒子中的位置。它使用的坐标系中，框的左上角是 (0,0)，框沿着水平 (x) 和垂直 (y) 轴定位。

> **备注：** 默认的背景位置值是 (0,0)。

最常见的背景位置值有两个单独的值——一个水平值后面跟着一个垂直值。

你可以使用像`top`和`right`这样的关键字 (在 {{cssxref("background-image")}} 页面上查找其他的关键字):

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top center;
}
```

或者使用 [长度值](/zh-CN/docs/Web/CSS/length) 和 [百分比](/zh-CN/docs/Web/CSS/percentage)：

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: 20px 10%;
}
```

你也可以混合使用关键字，长度值以及百分比，例如：

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top 20px;
}
```

最后，您还可以使用 4-value 语法来指示到盒子的某些边的距离——在本例中，长度单位是与其前面的值的偏移量。所以在下面的 CSS 中，我们将背景从顶部调整 20px，从右侧调整 10px:

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top 20px right 10px;
}
```

**使用下面的示例来处理这些值并在框内移动星星。**

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/position.html", '100%', 800)}}

> **备注：** `background-position` 是 {{cssxref("background-position-x")}} 和 {{cssxref("background-position-y")}} 的简写，它们允许您分别设置不同的坐标轴的值。

### 渐变背景

当渐变用于背景时，也可以使用像图像一样的 {{cssxref("background-image")}} 属性设置。

您可以在 MDN 的 [`<gradient>`](/zh-CN/docs/Web/CSS/gradient) 数据类型页面上，了解更多关于渐变的不同类型，以及使用它们可以做的事情。使用渐变的一个有趣方法是，使用 web 上可用的许多 CSS 渐变生成器之一，比如[这个](https://cssgradient.io/)。您可以创建一个渐变，然后复制并粘贴生成它的源代码。

在下面的示例中尝试一些不同的渐变。在这两个盒子里，我们分别有一个线性梯度，它延伸到整个盒子上，还有一个径向梯度，它有一个固定的大小，因此会重复。

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/gradients.html", '100%', 800)}}

### 多个背景图像

也可以有多个背景图像——在单个属性值中指定多个 `background-image` 值，用逗号分隔每个值。

当你这样做时，你可能会以背景图像互相重叠而告终。背景将与最后列出的背景图像层在堆栈的底部，背景图像在代码列表中最先出现的在顶端。

> **备注：** 渐变可以与常规的背景图像很好地混合在一起。

其它 `background-*` 属性，该属性值用逗号分隔的方式设置。例如下列 `background-image`：

```css
background-image: url(image1.png), url(image2.png), url(image3.png), url(image4.png);
background-repeat: no-repeat, repeat-x, repeat;
background-position: 10px 20px,  top right;
```

不同属性的每个值，将与其他属性中相同位置的值匹配。例如，上面的 image1 的 `background-repeat` 值将是 `no-repeat`。但是，当不同的属性具有不同数量的值时，会发生什么情况呢？答案是较小数量的值会循环—在上面的例子中有四个背景图像，但是只有两个背景位置值。前两个位置值将应用于前两个图像，然后它们将再次循环—image3 将被赋予第一个位置值，image4 将被赋予第二个位置值。

**我们来试一试。在下面的示例中包含了两个图像。为了演示叠加顺序，请尝试切换哪个背景图像在列表中最先出现。或使用其他属性更改位置、大小或重复值。**

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/multiple-background-image.html", '100%', 800)}}

### 背景附加

另一个可供选择的背景是指定他们如何滚动时，内容滚动。这是由 {{cssxref("background-attachment")}} 属性控制的，它可以接受以下值：

- `scroll`: 使元素的背景在页面滚动时滚动。如果滚动了元素内容，则背景不会移动。实际上，背景被固定在页面的相同位置，所以它会随着页面的滚动而滚动。
- `fixed`: 使元素的背景固定在视图端口上，这样当页面或元素内容滚动时，它就不会滚动。它将始终保持在屏幕上相同的位置。
- `local`: 这个值是后来添加的 (它只在 Internet Explorer 9+中受支持，而其他的在 IE4+中受支持)，因为滚动值相当混乱，在很多情况下并不能真正实现您想要的功能。局部值将背景固定在设置的元素上，因此当您滚动元素时，背景也随之滚动。

{{cssxref("background-attachment")}} 属性只有在有内容要滚动时才会有效果，所以我们做了一个示例来演示这三个值之间的区别——看看 [background-attachment.html](http://mdn.github.io/learning-area/css/styling-boxes/backgrounds/background-attachment.html) (或者看看这儿的 [源代码](https://github.com/mdn/learning-area/tree/master/css/styling-boxes/backgrounds)))。

### 使用 background 的简写

正如我在本课开始时提到的，您将经常看到使用 {{cssxref("background")}} 属性指定的背景。这种简写允许您一次设置所有不同的属性。

如果使用多个背景，则需要为第一个背景指定所有普通属性，然后在逗号后面添加下一个背景。在下面的例子中，我们有一个渐变，它指定大小和位置，然后是一个无重复的图像背景，它指定位置，然后是一个颜色。

这里有一些规则，需要在简写背景属性时遵循，例如：

- `background-color` 只能在逗号之后指定。
- `background-size` 值只能包含在背景位置之后，用'/'字符分隔，例如：`center/80%`。

查看 {{cssxref("background")}} 的 MDN 页面，以查看所有的注意事项。

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/background.html", '100%', 800)}}

### 背景的无障碍考虑

当你把文字放在背景图片或颜色上面时，你应该注意你有足够的对比度让文字对你的访客来说是清晰易读的。如果指定了一个图像，并且文本将被放置在该图像的顶部，您还应该指定一个`background-color` ，以便在图像未加载时文本也足够清晰。

屏幕阅读者不能解析背景图像，因此背景图片应该只是纯粹的装饰；任何重要的内容都应该是 HTML 页面的一部分，而不是包含在背景中。

## 边框

在学习盒子模型时，我们发现了边框如何影响盒子的大小。在这节课中，我们将看看如何创造性地使用边界。通常，当我们使用 CSS 向元素添加边框时，我们使用一个简写属性在一行 CSS 中设置边框的颜色、宽度和样式。我们可以使用 {{cssxref("border")}} 为一个框的所有四个边设置边框。

```css
.box {
  border: 1px solid black;
}
```

或者我们可以只设置盒子的一个边，例如：

```css
.box {
  border-top: 1px solid black;
}
```

这些简写的等价于：

```css
.box {
  border-width: 1px;
  border-style: solid;
  border-color: black;
}
```

也可以使用更加细粒度的属性：

```css
.box {
  border-top-width: 1px;
  border-top-style: solid;
  border-top-color: black;
}
```

> **备注：** 这些顶部、右侧、底部和左侧边框属性还具有与文档写入模式相关的映射逻辑属性 (例如，从左到右或从右到左的文本，或从上到下)。在下一课中，我们将探讨这些问题，这包括处理不同的文本指示 [详情](/zh-CN/docs/Learn/CSS/Building_blocks/Handling_different_text_directions)。

**有各种各样的样式可以用于边框。在下面的例子中，为框的四个边使用了不同的边框样式。调整边框样式、宽度和颜色，看看边框是如何工作的。**

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/borders.html", '100%', 800)}}

### 圆角

通过使用 {{cssxref("border-radius")}} 属性和与方框的每个角相关的长边来实现方框的圆角。可以使用两个长度或百分比作为值，第一个值定义水平半径，第二个值定义垂直半径。在很多情况下，您将只传递一个值，这两个值都将使用。

例如，要使一个盒子的四个角都有 10px 的圆角半径：

```css
.box {
  border-radius: 10px;
}
```

或使右上角的水平半径为 1em，垂直半径为 10％：

```css
.box {
  border-top-right-radius: 1em 10%;
}
```

我们在下面的示例中设置了所有四个角，然后更改右上角的值使之不同。您可以使用这些值来更改圆角样式。查看 {{cssxref("border-radius")}} 的属性页，查看可用的语法选项。

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/corners.html", '100%', 800)}}

## 玩转背景和边框

为了测试你的新知识，尝试使用背景和边框创建以下内容，使用下面的例子作为起点：

1. 给方框一个 5px 的黑色实心边框，圆角为 10px。
2. 添加一个背景图像 (使用 URL balloons.jpg)，并调整它的大小，使它能够覆盖盒子。
3. 给\<h2>一个半透明的黑色背景颜色，并使文本为白色。

{{EmbedGHLiveSample("css-examples/learn/backgrounds-borders/task.html", '100%', 800)}}

> **备注：** 你可以点击 [这里](https://github.com/mdn/css-examples/blob/master/learn/solutions.md)查看解决方案——但请先尝试一下自己能否实现。

## 总结

我们在这里已经介绍了很多，您可以看到有很多要添加背景或边框到盒子中。如果您想了解更多关于我们讨论过的特性的信息，请浏览不同的属性页面。MDN 上的每个页面都有更多的用法示例，供您玩转并增强您的知识。

在下一课中，我们将了解文档排版与 CSS 的相互影响。以及了解当文本不是从左向右流动时会发生什么？

{{PreviousMenuNext("Learn/CSS/Building_blocks/The_box_model", "Learn/CSS/Building_blocks/Handling_different_text_directions", "Learn/CSS/Building_blocks")}}

## 模块目录

1. [层叠与继承](/zh-CN/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
2. [CSS 选择器](/zh-CN/docs/Learn/CSS/Building_blocks/Selectors)

    - [标签，类，ID 选择器](/zh-CN/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors)
    - [属性选择器](/zh-CN/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors)
    - [伪类和伪元素](/zh-CN/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)
    - [关系选择器](/zh-CN/docs/Learn/CSS/Building_blocks/Selectors/Combinators)

3. [盒模型](/zh-CN/docs/Learn/CSS/Building_blocks/The_box_model)
4. [背景与边框](/zh-CN/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders)
5. [处理不同文字方向的文本](/zh-CN/docs/Learn/CSS/Building_blocks/Handling_different_text_directions)
6. [溢出的内容](/zh-CN/docs/Learn/CSS/Building_blocks/Overflowing_content)
7. [值和单位](/zh-CN/docs/Learn/CSS/Building_blocks/Values_and_units)
8. [在 CSS 中调整大小](/zh-CN/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS)
9. [图像、媒体和表单元素](/zh-CN/docs/Learn/CSS/Building_blocks/Images_media_form_elements)
10. [样式化表格](/zh-CN/docs/Learn/CSS/Building_blocks/Styling_tables)
11. [调试 CSS](/zh-CN/docs/Learn/CSS/Building_blocks/Debugging_CSS)
12. [组织 CSS](/zh-CN/docs/Learn/CSS/Building_blocks/Organizing)
