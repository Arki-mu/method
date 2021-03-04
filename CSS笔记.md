#### 公共样式

```css
*{
    margin: 0;
    padding: 0;
}
html,body{
    color: #333;
  	font-size: 16px;
    height: 100%;
    font-family: PingFang-SC-Regular;
}
a{
    text-decoration: none;/*去除下划线*/
    color:#212121;
}
ul,ol{
    list-style-type: none;/*清除样式（li前点·）*/
}
em,i{
    font-style: normal;/*清除文字样式*/
}
input,button{
    border: none;/*去除外边框（点击前）*/
    outline:none;/*去除外边框（点击后）*/
}
```

快捷键

alt+shift+F：格式化(快速整理)

Normalize.css：不同浏览器的默认样式存在差异，可以使用 Normalize.css抹平这些差异。

- 保留有用的默认值，不同于许多 CSS 的重置
- 标准化的样式，适用范围广的元素。
- 纠正错误和常见的浏览器的不一致性。
- 一些细微的改进，提高了易用性。
- 使用详细的注释来解释代码。

#### W3school CSS 属性选择器详解：

https://www.w3school.com.cn/css/css_selector_attribute.asp

```css
/*选取带有title属性的元素*/
[title]{}

/*选取带有title属性的p元素*/
p[title]{}

/*选取title属性值为important的元素*/
[title="important"]{}

/*选取title属性值包含important的元素*/
[title~="important"]{}

/*选取title属性值以important开头的元素 （该值必须是整个的单词）*/
[title|="important"]{}
```

###### 子串匹配属性选择器：

```css
/*选择href属性内以https开头的标签*/
[href^="https"]{}
/*选择href属性内含qq的标签*/
[href*="qq"]{}
/*选择href属性内以.com结尾的标签*/
[herf$=".com"]{}
```



#### 清除浮动的方法

```css
li{float:left;}
```

方法一：

```css
ul::after{
    display:table;/* 此元素会作为块级表格来显示（类似 <table>），表格前后带有换行符。*/
    content:"";
    clear:both;
}
```



#### 隐藏

不占位隐藏

```css
display:none;
```

占位隐藏(用在表格里就不占位)

visibility 属性规定元素是否可见。

提示：即使不可见的元素也会占据页面上的空间。请使用 "display" 属性来创建不占据页面空间的不可见元素。

```css
a{
    visibility:visible;/*默认值。元素是可见的*/
    visibility:hidden;/*元素是不可见的*/
    visibility:collapse;/*当在表格元素中使用时，此值可删除一行或一列，但是它不会影响表格的布局。被行或列占据的空间会留给其他内容使用。如果此值被用在其他的元素上，会呈现为 "hidden"。*/    
}
```



#### W3school CSS background 属性

https://www.w3school.com.cn/cssref/pr_background.asp

| 值                                                           | 描述                                             |
| ------------------------------------------------------------ | ------------------------------------------------ |
| *[background-color](https://www.w3school.com.cn/cssref/pr_background-color.asp)* | 规定要使用的背景颜色。                           |
| *[background-position](https://www.w3school.com.cn/cssref/pr_background-position.asp)* | 规定背景图像的位置。                             |
| *[background-size](https://www.w3school.com.cn/cssref/pr_background-size.asp)* | 规定背景图片的尺寸。                             |
| *[background-repeat](https://www.w3school.com.cn/cssref/pr_background-repeat.asp)* | 规定如何重复背景图像。                           |
| *[background-origin](https://www.w3school.com.cn/cssref/pr_background-origin.asp)* | 规定背景图片的定位区域。                         |
| *[background-clip](https://www.w3school.com.cn/cssref/pr_background-clip.asp)* | 规定背景的绘制区域。                             |
| *[background-attachment](https://www.w3school.com.cn/cssref/pr_background-attachment.asp)* | 规定背景图像是否固定或者随着页面的其余部分滚动。 |
| *[background-image](https://www.w3school.com.cn/cssref/pr_background-image.asp)* | 规定要使用的背景图像。                           |
| inherit                                                      | 规定应该从父元素继承 background 属性的设置。     |

###### background-attachment

```css
a{
    background-attachment: fixed;/*当页面的其余部分滚动时，背景图像不会移动。*/
	background-size: cover;/*默认值。背景图像会随着页面其余部分的滚动而移动。*/
}
```

###### background-position

需要把 background-attachment 属性设置为 "fixed"，才能保证该属性在 Firefox 和 Opera 中正常工作

```scss
a{
    background-repeat:no-repeat;/*背景图像将仅显示一次 其他repeat;repeat-x;repeat-y;*/
	background-attachment:fixed;
    background-position:center;/*居中*/
}
```



#### 文字超出省略

```css
/*一行*/
p{
    overflow: hidden;
    white-space: nowarp;
    text-overflow: ellipsis;
}
/*多行*/
p{
	overflow: hidden;
    display: -webkit-box;
  	-webkit-line-clamp: 2;/*规定行数*/
    -webkit-box-orient: vertical;
}
```

##### line-clamp:限制在一个块元素显示的文本的行数。

-webkit-line-clamp 是一个 不规范的属性（unsupported WebKit property），它没有出现在 CSS 规范草案中。

 为了实现该效果，它需要组合其他外来的WebKit属性。常见结合属性：

- display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
- -webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。
- text-overflow，可以用来多行文本的情况下，用省略号“...”隐藏超出范围的文本 。



#### transform 属性向元素应用 2D 或 3D 转换。

该属性允许我们对元素进行旋转、缩放、移动或倾斜。