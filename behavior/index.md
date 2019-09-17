#### 使用 vw 定制 rem 自适应布局

```
/* 基于UI width=750px DPR=2的页面 */
html{
    font-size: calc(100vw / 7.5)
}
```

#### 使用:nth-child 选择特定元素

```
li{
    &:nth-child(odd) { // 奇数
        background-color: $red;
    }
    &:nth-child(even) { // 偶数
        background-color: $purple;
    }
    &:nth-child(n+6):nth-child(-n+8) { // 第6个到第8个
        background-color: $green;
    }
    &:first-child{ // 第一个元素

    }
    &:last-child{ //最后一个元素

    }
}
```

#### 使用 writing-mode 排版竖文

#### 使用 text-align-last 对齐两端文本 \*

#### 使用:not 去除无用属性

```
.cleared-attr {
	li {
		height: 40px;
		line-height: 40px;
	}
	span {
		display: inline-block;
		color: $purple;
	}
	.first-line span:not(:last-child)::after { // 第一行除了最后一个元素，在每个元素后加 ，
		content: ",";
	}
	.second-line span:not(:nth-child(-n+3)) { // 第二行除了前三个都隐藏
		display: none;
	}
}
```

#### 使用 object-fit 规定图像尺寸

```
img {
		width: 100%;
		height: 260px;
		background-color: $green; // 图片填充不到的底色
		&.cover {
			object-fit: cover; // 被替换的内容在保持其宽高比的同时填充元素的整个内容框。
		}
		&.contain {
			object-fit: contain; // 被替换的内容将被缩放，以在填充元素的内容框时保持其宽高比。
		}
		&.fill {
			object-fit: fill; // 被替换的内容正好填充元素的内容框(极其可能被拉伸)
		}
		&.scale-down {
			object-fit: scale-down; // 内容的尺寸与 none 或 contain 中的一个相同，取决于它们两个之间谁得到的对象尺寸会更小一些。
		}
        &.none{
           object-fit: none; // 被替换的内容将保持其原有的尺寸。
        }
	}
}
```

#### 使用 text-overflow 控制文本溢出

- 其中包括单行文本溢出和多行文本溢出

#### 使用 transform 描绘 1px 边框

- 要点：分辨率比较低的屏幕下显示 1px 的边框会显得模糊，通过::before 或::after 和 transform 模拟细腻的 1px 边框

```
.thin { // 绘制的1px边框
	position: relative;
	&::after {
		position: absolute;
		left: 0;
		top: 0;
		border: 1px solid $red;
		width: 200%;
		height: 200%;
		content: "";
		transform: scale(.5);
		transform-origin: left top;
	}
}
```

#### 使用 transform 翻转内容

- 要点：通过 transform:scale3d()对内容进行翻转(水平翻转、垂直翻转、倒序翻转)
  [示范例子](https://codepen.io/JowayYoung/pen/NWKNZwO)

#### 使用 letter-spacing 排版倒序文本

```
.reverse-text {
	font-weight: bold;
	font-size: 50px;
	color: $red;
	letter-spacing: -100px; // letter-spacing最少是font-size的2倍
}
```

#### 使用 margin-left 排版左重右轻列表

- 要点：使用 flexbox 横向布局时，最后一个元素通过 margin-left:auto 实现向右对齐

```
.left-list {
	display: flex;
	align-items: center;
	padding: 0 10px;
	width: 600px;
	height: 60px;
	background-color: $green;
	li {
		padding: 0 10px;
		height: 40px;
		background-color: $orange;
		line-height: 40px;
		font-size: 16px;
		color: #fff;
		& + li {
			margin-left: 10px;
		}
		&:last-child {
			margin-left: auto;
		}
	}
}
```

[示例](https://codepen.io/JowayYoung/pen/PoYpROw)
