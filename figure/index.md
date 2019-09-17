#### 使用 div 绘制各种图形 \*\*

[示例](https://css-tricks.com/the-shapes-of-css/)

#### 使用 linear-gradient 描绘波浪线

[示例](https://codepen.io/JowayYoung/pen/EqEzwq)

#### 使用 repeating-linear-gradient 描绘彩带

```
.colour-bar {
	width: 500px;
	height: 50px;
	background-image: repeating-linear-gradient(90deg, $red, $red 50px, $purple 50px, $purple 100px);
}
```

#### 使用 conic-gradient 描绘饼图

```
.pie-chart {
	border-radius: 100%;
	width: 300px;
	height: 300px;
	background-image: conic-gradient($red 0 25%, $purple 25% 30%, $orange 30% 55%, $blue 55% 70%, $green 70% 100%);
}

```

#### 使用 linear-gradient 描绘方格背景

- 要点：使用 linear-gradient 绘制间断颜色的彩带进行交互生成方格

```
<div class="square-bg"></div>

.square-bg {
	width: 500px;
	height: 300px;
	background-image: linear-gradient(45deg, #eee 25%, transparent 25%, transparent 75%, #eee 75%),
		linear-gradient(45deg, #eee 25%, transparent 25%, transparent 75%, #eee 75%);
	background-position: 0 0, 20px 20px;
	background-size: 40px 40px;
}
```

#### 使用 box-shadow 裁剪图像

- 要点：通过 box-shadow 模拟蒙层实现中间镂空
- 场景：图片裁剪、新手引导、背景镂空、投射定位

```
<div class="img-cliper">
	<img src="https://yangzw.vip/static/codepen/gz.jpg">
	<div class="mask">
		<i></i>
	</div>
</div>

.img-cliper {
	overflow: hidden;
	position: relative;
	img {
		width: 400px;
	}
	i {
		position: absolute;
		left: 50px;
		top: 30px;
		border-radius: 100%;
		width: 100px;
		height: 50px;
		box-shadow: 0 0 0 9999px rgba(#000, .5);
	}
	.mask {
		position: absolute;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
	}
}
```

#### 使用 outline 描绘内边框

- 要点：通过 outline 设置轮廓进行描边，可设置 outline-offset 设置内描边
- 场景：内描边、外描边

```
.outside-border {
	outline: 10px dashed $blue;
	outline-offset: -50px;
	border: 10px dashed $orange;
	width: 300px;
	height: 300px;
	background-color: $green;
}
```
