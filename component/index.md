#### 下划线跟随导航栏

```
<div class="bruce flex-ct-x">
	<ul class="underline-navbar">
		<li>Alibaba阿里巴巴</li>
		<li>Tencent腾讯</li>
		<li>Baidu百度</li>
		<li>Jingdong京东</li>
		<li>Ant蚂蚁金服</li>
		<li>Netease网易</li>
	</ul>
</div>

.underline-navbar {
	display: flex;
	li {
		position: relative;
		padding: 10px;
		cursor: pointer;
		font-size: 20px;
		color: $blue;
		transition: all 300ms;
		&::before {
			position: absolute;
			left: 100%;
			top: 0;
			border-bottom: 2px solid transparent;
			width: 0;
			height: 100%;
			content: "";
			transition: all 300ms;
		}
		&:active {
			background-color: $blue;
			color: #fff;
		}
		&:hover {
			&::before {
				left: 0;
				top: 0;
				z-index: -1;
				border-bottom-color: $blue;
				width: 100%;
				transition-delay: 100ms;
			}
			& + li::before {
				left: 0;
			}
		}
	}
}
```

[示例](https://codepen.io/JowayYoung/pen/eYOJbNv)

#### 滚动指示器

- 要点：提示滚动进度的指示器
  [示范例子](https://codepen.io/JowayYoung/pen/ExYPMog)

#### 故障文本

- 要点：显示器故障形式的文本
- 场景：错误提示

```
<div class="fault-text" data-text="ERROR">ERROR</div>
.bruce {
	background-color: #000;
}
.fault-text {
	position: relative;
	font-weight: bold;
	font-size: 100px;
	color: #fff;
	&::before,
	&::after {
		overflow: hidden;
		position: absolute;
		top: 0;
		background-color: #000;
		clip: rect(0, 900px, 0, 0);
		color: #fff;
		content: attr(data-text);
		animation: shake 3s linear infinite alternate-reverse;
	}
	&::before {
		left: -2px;
		text-shadow: 1px 0 $blue;
	}
	&::after {
		left: 2px;
		text-shadow: -1px 0 $red;
		animation-duration: 2s;
	}
}
@keyframes shake {
	$steps: 20;
	@for $i from 0 through $steps {
		#{percentage($i * (1 / $steps))} {
			clip: rect(random(100) + px, 9999px, random(100) + px, 0);
		}
	}
}
```

### 换色器

- 要点：通过拾色器改变图像色相的换色器
- 场景：图片色彩变换
  [示例](https://codepen.io/JowayYoung/pen/vYBLqBm)

#### 状态悬浮球

- 要点：展示当前状态的悬浮球
- 场景：状态动态显示、波浪动画

```
<div class="state-ball">
	<div class="wave"></div>
</div>

.state-ball {
	overflow: hidden;
	position: relative;
	padding: 5px;
	border: 3px solid $green;
	border-radius: 100%;
	width: 150px;
	height: 150px;
	background-color: #fff;
	&::before,
	&::after {
		position: absolute;
		left: 50%;
		top: 0;
		z-index: 20;
		margin-left: -100px;
		width: 200px;
		height: 200px;
		content: "";
	}
	&::before {
		margin-top: -150px;
		border-radius: 45%;
		background-color: rgba(#fff, .5);
		animation: rotate 10s linear -5s infinite;
	}
	&::after {
		margin-top: -160px;
		border-radius: 40%;
		background-color: rgba(#fff, .8);
		animation: rotate 15s infinite;
	}
}
.wave {
	position: relative;
	border-radius: 100%;
	width: 100%;
	height: 100%;
	background-image: linear-gradient(-180deg, #af8 13%, $green 91%);
}
@keyframes rotate {
	from {
		transform: rotate(0);
	}
	to {
		transform: rotate(1turn);
	}
}
```

[示例](https://codepen.io/JowayYoung/pen/WNewOxa)

#### 粘粘球

```
<div class="sticky-ball">
	<div class="ball-1"></div>
	<div class="ball-2"></div>
</div>

.bruce {
	filter: contrast(10);
}
.sticky-ball {
	position: relative;
	width: 320px;
	height: 80px;
	filter: contrast(10);
}
div[class*=ball-] {
	position: absolute;
	top: 0;
	padding: 10px;
	border-radius: 100%;
	width: 80px;
	height: 80px;
	background-color: $red;
	filter: blur(5px);
	animation: 6s infinite;
}
.ball-1 {
	left: 0;
	animation-name: move-1 !important;
}
.ball-2 {
	left: 240px;
	animation-name: move-2 !important;
}
@keyframes move-1 {
	0%,
	20%,
	100% {
		width: 80px;
		height: 80px;
	}
	50% {
		left: 110px;
		top: -15px;
		width: 110px;
		height: 110px;
	}
	85% {
		left: 75px;
		width: 90px;
		height: 70px;
	}
	90% {
		top: -2px;
		width: 75px;
		height: 85px;
	}
}
@keyframes move-2 {
	0%,
	20%,
	100% {
		width: 80px;
		height: 80px;
	}
	50% {
		left: 110px;
		top: -15px;
		width: 110px;
		height: 110px;
	}
	85% {
		left: 165px;
		width: 90px;
		height: 70px;
	}
	90% {
		top: -2px;
		width: 75px;
		height: 85px;
	}
}
```

[示例](https://codepen.io/JowayYoung/pen/zYOqdBz)

#### 商城票券

- 要点：边缘带孔和中间折痕的票劵
- 场景：电影票、代金券、消费卡

```
<div class="mall-ticket">
	<h3>100元</h3>
	<p>网易考拉代金券</p>
</div>

.mall-ticket {
	display: flex;
	position: relative;
	width: 300px;
	height: 100px;
	background: radial-gradient(circle at right top, transparent 10px, $red 0) top left/100px 51% no-repeat,
		radial-gradient(circle at right bottom, transparent 10px, $red 0) bottom left/100px 51% no-repeat,
		radial-gradient(circle at left top, transparent 10px, #ccc 0) top right/200px 51% no-repeat,
		radial-gradient(circle at left bottom, transparent 10px, #ccc 0) bottom right/200px 51% no-repeat;
	filter: drop-shadow(2px 2px 2px rgba(#fff, .2));
	line-height: 100px;
	text-align: center;
	color: #fff;
	&::before {
		position: absolute;
		left: 100px;
		top: 0;
		bottom: 0;
		margin: auto;
		border: 1px dashed $purple;
		height: 80px;
		content: "";
	}
	&::after {
		position: absolute;
		left: 100%;
		top: 0;
		width: 5px;
		height: 100%;
		background-image: linear-gradient(180deg, #ccc 5px, transparent 5px, transparent),
			radial-gradient(10px circle at 5px 10px, transparent 5px, #ccc 5px);
		background-size: 5px 15px;
		content: "";
	}
	h3 {
		width: 100px;
		font-size: 30px;
	}
	p {
		flex: 1;
		font-weight: bold;
		font-size: 18px;
	}
}
```

[示范例子](https://codepen.io/JowayYoung/pen/rNBeYza)

#### 倒影加载条

- 要点：带有渐变倒影的加载条
- 场景：加载提示

```
<ul class="reflect-loading">
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
		<li></li>
</ul>

$count: 10;
$color: $purple $blue;

.reflect-loading {
	display: flex;
	height: 100px;
	-webkit-box-reflect: below 0 linear-gradient(rgba(#fff, 0), rgba(#fff, .7));
	li {
		width: 20px;
		@for $i from 0 to $count {
			$args: append($color, $i * 100% / ($count - 1));
			&:nth-child(#{$i + 1}) {
				background-color: mix($args...);
				animation: rotate 3s cubic-bezier(.81, .04, .4, .7) infinite;
				animation-delay: $i * 50ms;
			}
		}
	}
}
@keyframes rotate {
	0% {
		transform: rotate(-.5turn) rotateX(-1turn);
	}
	75%,
	100% {
		transform: none;
	}
}
```

[示例](https://codepen.io/JowayYoung/pen/GRKZzpg)

#### 三维立方体

[示例](https://codepen.io/JowayYoung/pen/PoYNgXY)

#### 星级评分

[示例](https://codepen.io/JowayYoung/pen/MWgjGMj)

#### 加载指示器

```
<div class="load-indicator">加载中<dot></dot></div>

.load-indicator {
	font-size: 16px;
	color: $blue;
	dot {
		display: inline-block;
		overflow: hidden;
		height: 1em;
		line-height: 1;
		vertical-align: -.25em;
		&::after {
			display: block;
			white-space: pre-wrap;
			content: "...\A..\A.";
			animation: loading 3s infinite step-start both;
		}
	}
}
@keyframes loading {
	33% {
		transform: translate3d(0, -2em, 0);
	}
	66% {
		transform: translate3d(0, -1em, 0);
	}
}
```

#### 自适应相册

- 要点：自适应照片数量的相册
- 场景：九宫格相册、微信相册、图集

[示例](https://codepen.io/JowayYoung/pen/pozNGyj)

#### 螺纹进度条

[示例](https://codepen.io/JowayYoung/pen/GRKrJJX)

#### 蛇形边框

[示例](https://codepen.io/JowayYoung/pen/GRKmgZZ)

#### 自动打字

[示例](https://codepen.io/JowayYoung/pen/ZEzKQEx)

#### https://codepen.io/JowayYoung/pen/ZEzKQEx

[示范](https://codepen.io/JowayYoung/pen/PoYpaLL)
