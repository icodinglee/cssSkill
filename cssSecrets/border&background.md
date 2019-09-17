#### 半透明边框

- background-clip

```
<main>
    <div>A paragraph of filler text. La la la de dah de dah de dah de la.</div>
</main>
main{
    width: 100%;
    padding: 60px 80px 80px;
    background:red;
}
div{
    padding: 12px;
    margin: 20px auto;
    background: white;
    border: 10px solid hsla(0, 0%, 100%, .5);
    background-clip: padding-box;  ***重点
}
```

#### 多重边框

- outline outline-offset

```
div{
    width: 200px; height: 120px;
    background: #efebe9;
    border: 5px solid #B4A078;
    outline: #B4A078 dashed 1px;
    outline-offset: -10px;
    margin-bottom: 20px;
  }
```

#### 内圆角

- outline box-shadow

```
 div{
    width: 209px;
    margin: 29px auto;
    padding: 8px 16px;
    border-radius: 8px;
    background: #f4f0ea;
    outline: 6px solid #b4a078;
    box-shadow: 0 0 0 5px #b4a078;
}

```

#### 背景位置的三种写法

```
 div{
    width: 229px; height: 139px;
    margin: auto;
    color: #f4f0ea;
    padding: 16px 29px 28px 20px;
    background: #b4a078 url('static/player_logo@2x.png') no-repeat bottom right / 78px 21px;  // 着重注意这里的 斜杠 /
  }
  div:nth-of-type(1){
    background-position: right 29px bottom 28px;
  }
  div:nth-of-type(2){
    background-origin: content-box;
  }
  div:nth-of-type(3){
    background-position: calc(100% - 29px) calc(100% - 28px);
  }
```

[示例](https://lhammer.cn/You-need-to-know-css/#/extended-bg-position)

#### 条纹背景

##### 进度条

```
 <div class="progress-outer">
    <div class="progress-enter">
        <div class="progress-bg"></div>
    </div>
</div>

.progress-outer {
    width: 60%; height: 12px;
    border-radius: 8px;
    overflow: hidden;
    position: relative;
  }
  .progress-enter {
    height: inherit;
    background: rgba(180, 160, 120, .2);
  }
  .progress-bg {
    width: 60%; height: inherit;
    border-radius: 6px;
    background: repeating-linear-gradient(-45deg, #D9CFBB  25%, #C3B393 0, #C3B393 50%, #D9CFBB 0, #D9CFBB 75%, #C3B393 0);   * 画出条纹背景
    background-size: 16px 16px;
    animation: panoramic 20s linear infinite;
  }
  @keyframes panoramic{
    to {
      background-position: 200% 0;
    }
  }
```

##### 购物卡券 上部分切圆

- radial-gradient

```
<div class="coupon-card"></div>

.coupon-card {
    width: 200px;
    height: 120px;
    background-image: radial-gradient(circle at 100px -8px, transparent 20px, #b4a078 21px);
  }
```

#### 1px 细线

- box-shadow + transform

```
 <span class="one-pixel-line shadow"></span>

  span.one-pixel-line {
    width: 229px;
    position: relative;
  }
  span.one-pixel-line::after {
    content: '';
    width: 229px;
    position: absolute;
    bottom: 0; left: 0;
    box-shadow: 0 0 0 1px #b4a078;
    transform-origin: 0 bottom;
    transform: scaleY(.5) translateZ(0);
  }
  @media (min-resolution: 2dppx) {
    span.one-pixel-line.shadow::after {
      box-shadow: 0 0 0 .5px #b4a078;
    }
  }
  @media (min-resolution: 3dppx) {
    span.one-pixel-line.shadow::after {
      box-shadow: 0 0 0 .333333px #b4a078;
    }
  }

```

- border + pseudo-element + transform 推荐使用

```
<style>
  main {
    width: 100%;
    padding: 52px 29px;
    display: flex;
    justify-content: center;
  }
  span.one-pixel-line {
    display: block;
    width: 229px; height: 229px;
    position: relative;
  }
  span.one-pixel-line.right,
  span.one-pixel-line.bottom,
  span.one-pixel-line.left {
    margin-left: -229px;
  }
  span.one-pixel-line::before,
  span.one-pixel-line::after {
    content: "";
    display: block;
    position: absolute;
    transform-origin: 0 0;
  }
  /* top line */
  span.one-pixel-line.top::before {
    width: 100%;
    top: 0; left: 0;
    border-top: 1px solid #b4a078;
    transform-origin: 0 top;
  }
  @media (min-resolution: 2dppx) {
    span.one-pixel-line.top::before {
      width: 200%;
      transform: scale(.5) translateZ(0);
    }
  }
  @media (min-resolution: 3dppx) {
    span.one-pixel-line.top::before {
      width: 300%;
      transform: scale(.333333) translateZ(0);
    }
  }
  /* right line */
  span.one-pixel-line.right::after {
    height: 100%;
    top: 0; right: 0;
    border-right: 1px solid #b4a078;
    transform-origin: right 0;
  }
  @media (min-resolution: 2dppx) {
    span.one-pixel-line.right::after {
      height: 200%;
      transform: scale(.5) translateZ(0);
    }
  }
  @media (min-resolution: 3dppx) {
    span.one-pixel-line.right::after {
      height: 300%;
      transform: scale(.333333) translateZ(0);
    }
  }
  /* bottom line */
  span.one-pixel-line.bottom::after {
    width: 100%;
    bottom: 0; left: 0;
    border-bottom: 1px solid #b4a078;
    transform-origin: 0 bottom;
  }
  @media (min-resolution: 2dppx) {
    span.one-pixel-line.bottom::after {
      width: 200%;
      transform: scale(.5) translateZ(0);
    }
  }
  @media (min-resolution: 3dppx) {
    span.one-pixel-line.bottom::after {
      width: 300%;
      transform: scale(.333333) translateZ(0);
    }
  }
  /* left line */
  span.one-pixel-line.left::before {
    height: 100%;
    top: 0; left: 0;
    border-left: 1px solid #b4a078;
    transform-origin: 0 left;
  }
  @media (min-resolution: 2dppx) {
    span.one-pixel-line.left::before {s
      height: 200%;
      transform: scale(.5) translateZ(0);
    }
  }
  @media (min-resolution: 3dppx) {
    span.one-pixel-line.left::before {
      height: 300%;
      transform: scale(.333333) translateZ(0);
    }
  }
</style>
<template>
  <main class="main">
    <span class="one-pixel-line top"></span>
    <span class="one-pixel-line right"></span>
    <span class="one-pixel-line bottom"></span>
    <span class="one-pixel-line left"></span>
  </main>
</template>
<script>
</script>
```
