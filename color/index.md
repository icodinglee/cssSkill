#### 使用 color 改变边框颜色

- border 没有定义 border-color 时，设置 color 后， border-color 会被设置为 color

```
.elem {
    border: 1px solid;
    color: #f66;
}
```

#### 使用::selection 改变文本选择颜色

#### 使用 linear-gradient 控制文本渐变

```
<h1 class="gradient-text">Full Stack Developer</h1>

.gradient-text {
	background-image: linear-gradient(90deg, $red, $orange);
   background-clip: text;
	line-height: 60px;
	font-size: 60px;
	animation: hue 5s linear infinite;
	-webkit-text-fill-color: transparent;
}
@keyframes hue {
	from {
		filter: hue-rotate(0);
	}
	to {
		filter: hue-rotate(-1turn);
	}
}
```

#### 使用 caret-color 改变光标颜色

#### 使用:scrollbar 改变滚动条样式

```
div{
    &::-webkit-scrollbar {
		width: 5px;
	}
	&::-webkit-scrollbar-track {
		background-color: #f0f0f0;
	}
	&::-webkit-scrollbar-thumb {
		border-radius: 2px;
		background-color: purple;
	}
}
```
