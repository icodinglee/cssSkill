#### 快速重置表单默认样式

```
button { all: unset; }
```

#### 文本省略号显示

```
div {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box; /* 将对象作为弹性伸缩盒子模型显示 */
  -webkit-line-clamp: 4; /* 控制最多显示几行 */
  -webkit-box-orient: vertical; /* 设置或检索伸缩盒对象的子元素的排列方式 */
}
```

#### 最后一个元素不显示某个样式

```
div:not(:last-child) /* 匹配非最后一个 div 元素的 div 元素 */
```

#### 设置文本两端对齐

```
div {
     width: 100px;
     padding: 0 10px;
     background: pink;
     margin-bottom: 10px;
     text-align-last:justify; /* 这是关键属性 */
}

<div>账号</div>
<div>密码设置</div>
<div>手机号</div>
```

#### 单选框复选框样式

```
<input type="checkbox" id="check" name="check" />
<label for="check">Checkbox</label>

input[type=checkbox] {display: none;}

input[type=checkbox] + label:before {
    content: "";
    border: 1px solid #000;
    font-size: 11px;
    line-height: 10px;
    margin: 0 5px 0 0;
    height: 10px;
    width: 10px;
    text-align: center;
    vertical-align: middle;
}

input[type=checkbox]:checked + label:before {
    content: "\2713";
}
```

#### 不使用图片的菜单图标

```
.gradient-icon {
    background: linear-gradient(to bottom, #000 0%, #000 20%, transparent 20%, transparent 40%, #000 40%, #000 60%, transparent 60%, transparent 80%, #000 80%, #000 100%);
}
```

#### 垂直方向的百分比边距(margin; padding)

- 实际上垂直方向的排列计算是基于父元素的宽度而不是高度。
- 子元素的百分比是相对于父元素的宽度。

#### 渐变边框

要使用渐变边框非常简单，只需要设置一个更低 z-index 的伪元素即可：

```
.box {
  margin: 80px 30px;
  width: 200px;
  height: 200px;
  position: relative;
  background: #fff;
  float: left;
}
.box:before {
      content: '';
      z-index: -1;
      position: absolute;
      width: 220px;
      height: 220px;
      top: -10px;
      left: -10px;
      background-image: linear-gradient(90deg, yellow, gold);
}
```

#### 支持过渡属性的 z-index

#### visibility: visible

- 把一个设置为 visibility: visible 的元素放在一个设置为 visibility: hidden 的元素里面，会发生什么？整个父元素都被隐藏了，而子元素不会。

#### 用 CSS 动画实现省略号动画

```
.loading:after {
    overflow: hidden;
    display: inline-block;
    vertical-align: bottom;
    animation: ellipsis 2s infinite;
    content: "\2026"; /* ascii code for the ellipsis character */
}
@keyframes ellipsis {
    from {
        width: 2px;
    }
    to {
        width: 15px;
    }
}

```

#### CSS 引用模板

```
.box-shadow {
    background-color: #FF8020;
    width: 160px;
    height: 90px;
    margin-top: -45px;
    margin-left: -80px;
    position: absolute;
    top: 50%;
    left: 50%;
}
.box-shadow:after {
    content: "";
    width: 150px;
    height: 1px;
    margin-top: 88px;
    margin-left: -75px;
    display: block;
    position: absolute;
    left: 50%;
    z-index: -1;
    -webkit-box-shadow: 0px 0px 8px 2px #000000;
       -moz-box-shadow: 0px 0px 8px 2px #000000;
            box-shadow: 0px 0px 8px 2px #000000;
}

```

#### 通用媒体查询

```
/* Smartphones (portrait and landscape) ----------- */
@media only screen
and (min-device-width : 320px) and (max-device-width : 480px) {
  /* Styles */
}

/* Smartphones (landscape) ----------- */
@media only screen and (min-width : 321px) {
  /* Styles */
}

/* Smartphones (portrait) ----------- */
@media only screen and (max-width : 320px) {
  /* Styles */
}

/* iPads (portrait and landscape) ----------- */
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) {
  /* Styles */
}

/* iPads (landscape) ----------- */
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) {
  /* Styles */
}

/* iPads (portrait) ----------- */
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) {
  /* Styles */
}

/* Desktops and laptops ----------- */
@media only screen and (min-width : 1224px) {
  /* Styles */
}

/* Large screens ----------- */
@media only screen and (min-width : 1824px) {
  /* Styles */
}

/* iPhone 4 ----------- */
@media only screen and (-webkit-min-device-pixel-ratio:1.5), only screen and (min-device-pixel-ratio:1.5) {
  /* Styles */
}

```

#### 现代字体栈

```
/* Times New Roman-based serif */
font-family: Cambria, "Hoefler Text", Utopia, "Liberation Serif", "Nimbus Roman No9 L Regular", Times, "Times New Roman", serif;

/* A modern Georgia-based serif */
font-family: Constantia, "Lucida Bright", Lucidabright, "Lucida Serif", Lucida, "DejaVu Serif," "Bitstream Vera Serif", "Liberation Serif", Georgia, serif;

/*A more traditional Garamond-based serif */
font-family: "Palatino Linotype", Palatino, Palladio, "URW Palladio L", "Book Antiqua", Baskerville, "Bookman Old Style", "Bitstream Charter", "Nimbus Roman No9 L", Garamond, "Apple Garamond", "ITC Garamond Narrow", "New Century Schoolbook", "Century Schoolbook", "Century Schoolbook L", Georgia, serif;

/*The Helvetica/Arial-based sans serif */
font-family: Frutiger, "Frutiger Linotype", Univers, Calibri, "Gill Sans", "Gill Sans MT", "Myriad Pro", Myriad, "DejaVu Sans Condensed", "Liberation Sans", "Nimbus Sans L", Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif;

/*The Verdana-based sans serif */
font-family: Corbel, "Lucida Grande", "Lucida Sans Unicode", "Lucida Sans", "DejaVu Sans", "Bitstream Vera Sans", "Liberation Sans", Verdana, "Verdana Ref", sans-serif;

/*The Trebuchet-based sans serif */
font-family: "Segoe UI", Candara, "Bitstream Vera Sans", "DejaVu Sans", "Bitstream Vera Sans", "Trebuchet MS", Verdana, "Verdana Ref", sans-serif;

/*The heavier "Impact" sans serif */
font-family: Impact, Haettenschweiler, "Franklin Gothic Bold", Charcoal, "Helvetica Inserat", "Bitstream Vera Sans Bold", "Arial Black", sans-serif;

/*The monospace */
font-family: Consolas, "Andale Mono WT", "Andale Mono", "Lucida Console", "Lucida Sans Typewriter", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Liberation Mono", "Nimbus Mono L", Monaco, "Courier New", Courier, monospace;

```

#### 锚链接伪类

```
a:link { color: blue; }
a:visited { color: purple; }
a:hover { color: red; }
a:active { color: yellow; }

```

#### CSS3：全屏背景

```
html {
    background: url('images/bg.jpg') no-repeat center center fixed;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
}

```

#### @font-face 模板

```
@font-face {
    font-family: 'MyWebFont';
    src: url('webfont.eot'); /* IE9 Compat Modes */
    src: url('webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('webfont.woff') format('woff'), /* Modern Browsers */
    url('webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
    url('webfont.svg#svgFontName') format('svg'); /* Legacy iOS */
}

body {
    font-family: 'MyWebFont', Arial, sans-serif;
}

```

#### currentColor 当前的标签所继承的文字颜色

#### png 图片如何改颜色

- 在 chrome 浏览器下，如果一个元素的主体部分，无论以何种方式，只要在页面中不可见，其 drop-shadow 是不可见的。实体部分哪怕有 1px 可见，则 drop-shadow 完全可见。

```
<i class="icon">
    <i class="icon icon-del"></i>
</i>

.icon {
  display: inline-block;
  width: 20px;
  height: 20px;
  overflow: hidden;
}
.icon-del {
  background: url(delete.png) no-repeat center;
}
.icon > .icon {
  position: relative;
  left: -20px;
  border-right: 20px solid transparent;
  -webkit-filter: drop-shadow(20px 0);
  filter: drop-shadow(20px 0);
}
```

#### 如何去掉 chrome input 的背景黄色

```
input:-webkit-autofill {
  -webkit-box-shadow: 0 0 0px 1000px rgba(255, 255, 255, 0.5) inset !important;
}
```

#### chrome 中设置小于 12px 的字体

```
ant-checkbox-wrapper {
 cursor: pointer;
 font-size: 10px;
 display: inline-block;
 -webkit-text-size-adjust: none; // 不支持
 transform: scale(0.9);
}
```

#### border 颜色渐变

```
border-color:red green blue pink;
```

#### 0.5px border

```
.div::after {
  content: " ";
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 1px;
  background-image: linear-gradient(0deg, transparent 50%, #e0e0e0 50%);
}

div::after{
  content: "";
  display: block;
  position: absolute;
  left: -50%;
  bottom: 0;
  width: 200%;
  height: 1px;
  background: #c3c3c3;
  -webkit-transform: scale(0.5);
}
```
