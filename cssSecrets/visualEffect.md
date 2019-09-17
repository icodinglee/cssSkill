#### 非常规阴影

```
箭头向右侧整体带阴影的气泡
.arrowBubble {
    width: 228px;
    height: 180px;
    margin-bottom: 29px;
    background: #b4a078;
    position: relative;
    border-radius: 5px;
    filter: drop-shadow(2px 2px 2px rgba(180, 160, 120, 0.9));
}
.arrowBubble::before {
    content: "";
    position: absolute;
    width: 0;
    height: 0;
    top: 65px;
    right: -20px;
    border: 22px solid transparent;
    border-left-color: #b4a078;
    border-right-width: 0;
}

带阴影的圆点边框
div{
    width: 228px;
    height: 180px;
    margin-bottom: 29px;
    background: #b4a078;
    position: relative;
    background: transparent;
    border: 6px dotted #b4a078;
    filter: drop-shadow(2px 2px 2px rgba(180, 160, 120, 0.9));
}
```

#### 文本效果

[示例](https://lhammer.cn/You-need-to-know-css/#/text-effects)

#### 环形文字

- 利用 svg, 把文字贴合到路径

```
 <main>
    <svg viewBox="0 0 100 100">
      <path d="M 0,50 a 50,50 0 1,1 0,1 z" id="circle" />
      <text>
        <textPath xlink:href="#circle">
          You-need-to-know-css-tricks-You-need-to-know-css-tricks-You-
        </textPath>
      </text>
    </svg>
</main>

main {
    width: 289px; height: 289px;
    margin: 80px auto;
    font-size: 12px;
}
main svg {
    overflow: visible;
    animation: circular-text-rotate 5s linear paused infinite;
}
main svg:hover {
    animation-play-state: running;
}
main path {
    fill: none;
}
main text {
    fill: #b4a078;
}
@keyframes circular-text-rotate {
    to {
      transform: rotate(1turn);
    }
}

```

#### css 实现换行操作

- 使用 \A 借助伪元素进行换行

```
<span class="key">👦🏿Name:</span>
<span class="bold">LHammer</span>
<span class="key br">👨🏼‍💻GitHub:</span>
<span class="bold">https://github.com/l-hammer</span>

span.key {
    padding-right: 6px;
}
span.bold {
    line-height: 2em;
    font-weight: bold;
}
span.br::before {
    content: "\A";     * 这是重点
    white-space: pre;  * 这是重点
}
span.bold + span.bold::before {
    content: ", ";
    font-weight: 500;
    margin-left: -.25em;
}
```
