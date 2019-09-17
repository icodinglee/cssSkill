#### 使用 overflow-scrolling 支持弹性滚动

- 要点：iOS 页面非 body 元素的滚动操作会非常卡(Android 不会出现此情况)，通过 overflow-scrolling:touch 调用 Safari 原生滚动来支持弹性滚动，增加页面滚动的流畅度

```
body {
    -webkit-overflow-scrolling: touch;
}
.elem {
    overflow: auto;
}
复
```

#### 使用 transform 启动 GPU 硬件加速

- 有时执行动画可能会导致页面卡顿，可在特定元素中使用硬件加速来避免这个问题

```
.elem {
    transform: translate3d(0, 0, 0); /* translateZ(0)亦可 */
}
```

#### 使用 attr()抓取 data-\*

- 在标签上自定义属性 data-\*，通过 attr()获取其内容赋值到 content 上

#### 使用:valid 和:invalid 校验表单

- <input>使用伪类:valid 和:invalid 配合 pattern 校验表单输入的内容

```
<form class="form-validation">
	<div>
		<label>名字</label>
		<input type="text" placeholder="请输入你的名字(1到10个中文)" pattern="^[\u4e00-\u9fa5]{1,10}$" required>
	</div>
</form>

.form-validation {
	width: 500px;
	label {
		display: block;
		padding-bottom: 5px;
		font-weight: bold;
		font-size: 16px;
	}
	input {
		display: block;
		padding: 0 20px;
		outline: none;
		border: 1px solid #ccc;
		width: 100%;
		height: 40px;
		caret-color: $blue;
		transition: all 300ms;
		&:valid {
			border-color: $green;
			box-shadow: inset 5px 0 0 $green;
		}
		&:invalid {
			border-color: $red;
			box-shadow: inset 5px 0 0 $red;
		}
	}

}
```

[示例](https://codepen.io/JowayYoung/pen/QemxKr)

#### 使用 pointer-events 禁用事件触发

#### 使用+或~美化选项框

- <label>使用+或~配合 for 绑定 radio 或 checkbox 的选择行为
- 可用于选项框美化、选中项增加选中样式

```
<div class="bruce flex-ct-x">
	<ul class="beauty-selection">
		<li>
			<input type="radio" name="radioName" id="fed-engineer" hidden>
			<label for="fed-engineer"></label>
			<span>前端工程师</span>
		</li>
		<li>
			<input type="radio" name="radioName" id="fsd-engineer" hidden>
			<label for="fsd-engineer"></label>
			<span>全栈工程师</span>
		</li>
	</ul>
</div>

.beauty-selection {
	display: flex;
	li {
		display: flex;
		align-items: center;
		margin-left: 20px;
		&:first-child {
			margin-left: 0;
		}
	}
	input:checked + label {
		background-color: $orange;
	}
	label {
		margin-right: 5px;
		padding: 2px;
		border: 1px solid $orange;
		border-radius: 100%;
		width: 18px;
		height: 18px;
		background-clip: content-box;
		cursor: pointer;
		transition: all 300ms;
		&:hover {
			border-color: $blue;
			background-color: $blue;
			box-shadow: 0 0 7px $blue;
		}
	}
	span {
		font-size: 16px;
	}
}
```

#### 使用 max-height 切换自动高度

- 要点：通过 max-height 定义收起的最小高度和展开的最大高度，设置两者间的过渡切换
- 场景：隐藏式子导航栏、悬浮式折叠面板

```
<div class="bruce flex-ct-x">
	<ul class="auto-height">
		<li>
			<h3>列表1</h3>
			<p>内容1<br>内容2<br>内容3<br>内容4</p>
		</li>
		<li>
			<h3>列表2</h3>
			<p>内容1<br>内容2<br>内容3<br>内容4</p>
		</li>
		<li>
			<h3>列表3</h3>
			<p>内容1<br>内容2<br>内容3<br>内容4</p>
		</li>
	</ul>
</div>

.auto-height {
	width: 300px;
	li {
		margin-top: 5px;
		cursor: pointer;
		&:first-child {
			margin-top: 0;
		}
		&:hover p {
			border-bottom-width: 1px;
			max-height: 600px;
		}
	}
	h3 {
		padding: 0 20px;
		height: 40px;
		background-color: $red;
		cursor: pointer;
		line-height: 40px;
		font-size: 16px;
		color: #fff;
	}
	p {
		overflow: hidden;
		padding: 0 20px;
		border: 1px solid $red;
		border-top: none;
		border-bottom-width: 0;
		max-height: 0;
		line-height: 30px;
		transition: all 500ms;
	}
}
```

[示例](https://codepen.io/JowayYoung/pen/NQYJpm)

#### 使用 resize 拉伸分栏

- 要点：通过 resize 设置横向自由拉伸来调整目标元素的宽度
- 场景：富文本编辑器、分栏阅读

```
<div class="bruce flex-ct-x">
	<div class="stretching-column">
		<div class="left">
			<div class="resize-bar"></div>
			<div class="resize-line"></div>
			<div class="resize-text">ABCDEFGHIJKLMNOPQRSTUVWXYZ</div>
		</div>
		<div class="right">ABCDEFGHIJKLMNOPQRSTUVWXYZ</div>
	</div>
</div>

.stretching-column {
	overflow: hidden;
	border: 1px solid $blue;
	width: 600px;
	height: 300px;
	line-height: 20px;
	font-size: 16px;
	color: $orange;
	.left {
		overflow: hidden;
		float: left;
		position: relative;
		height: 100%;
	}
	.right {
		overflow: hidden;
		padding: 10px;
		height: 100%;
		background-color: #f0f0f0;
		word-break: break-all;
	}
}
.resize-bar {
	overflow: scroll;
	width: 200px;
	height: 100%;
	opacity: 0;
	resize: horizontal;
	&::-webkit-scrollbar {
		width: 200px;
		height: 100%;
	}
	&:hover,
	&:active {
		& ~ .resize-line {
			border-left: 1px dashed $blue;
		}
	}
}
.resize-line {
	position: absolute;
	right: 0;
	top: 0;
	bottom: 0;
	border-left: 1px solid #ccc;
	border-right: 2px solid #f0f0f0;
	pointer-events: none;
}
.resize-text {
	overflow-x: hidden;
	position: absolute;
	left: 0;
	right: 5px;
	top: 0;
	bottom: 0;
	padding: 10px;
	word-break: break-all;
}
```
