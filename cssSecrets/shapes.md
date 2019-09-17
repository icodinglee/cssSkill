#### 椭圆 && 半圆

- border-radius

```
<style>
  main {
    width: 100%;
    padding: 60px 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  div {
    width: 200px; height: 150px;
    background: #b4a078;
    margin-bottom: 30px;
  }
  .ellipse:nth-of-type(1) {
    width: 300px; height: 150px;
    border-radius: 50% / 100% 100% 0 0;
  }
  .ellipse:nth-of-type(2) {
    width: 150px; height: 150px;
    border-radius: 100% 0 0 0;
  }
  .ellipse:nth-of-type(3) {
    border-radius: 50% / 100% 100% 0 0;
  }
  .ellipse:nth-of-type(4) {
    width: 100px;
    border-radius: 100% 0 0 0;
  }
  .ellipse:nth-of-type(5) {
    width: 300px;
    border-radius: 50% / 0 100%;
  }
  .ellipse:nth-of-type(6) {
    width: 300px;
    border-radius: 50% / 100% 0;
  }
</style>
<template>
  <main>
    <div class="ellipse">上半圆</div>
    <div class="ellipse">左上四分之一圆</div>
    <div class="ellipse">上半椭圆</div>
    <div class="ellipse"></div>
    <div class="ellipse"></div>
    <div class="ellipse"></div>
  </main>
</template>
<script>
</script>
```

#### 平行四边形

- transform clip-path

```
// 平行四边形内带文字
 <div class="diamond">
    <div>diamond</div>
 </div>
.diamond > div::before{
    content: "";
    position: absolute;
    top: 0; left: 0; bottom: 0; right: 0;
    z-index: -1;
    transform: skewX(-45deg);
    background: #b4a078;
  }

// 菱形裁剪图片
<div class="diamond">
    <img src="static/dog2018.jpg" alt="">
</div>

.diamond > img{
    width: 300px; height: 150px;
    clip-path: polygon(50% 0, 100% 50%, 50% 100%, 0 50%);
    transition: 1s clip-path;
}
.diamond > img:hover{
    clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
}
```

#### 折角

- gradient, clip-path

```
// 折角 background-size + linear-gradient
div {
    background: linear-gradient(45deg, transparent 12px, #b4a078 13px) bottom left, linear-gradient(135deg, transparent 12px, #b4a078 13px) top left, linear-gradient(-135deg, transparent 12px, #b4a078 13px) top right, linear-gradient(-45deg, transparent 12px, #b4a078 13px) bottom right;
    background-size: 51% 51%;
    background-repeat: no-repeat;
}

// 圆弧角 radial-gradient +  background-size
div{
    background: radial-gradient( circle at bottom left, transparent 15px, #b4a078 16px ) bottom left, radial-gradient(circle at top left, transparent 15px, #b4a078 16px) top left, radial-gradient(circle at top right, transparent 15px, #b4a078 16px) top right, radial-gradient(circle at bottom right, transparent 15px, #b4a078 16px) bottom right;
    background-size: 51% 51%;
    background-repeat: no-repeat;
}

// clip-path实现折角
div {
    clip-path: polygon( 20px 0, calc(100% - 20px) 0, 100% 20px, 100% calc(100% - 20px), calc(100% - 20px) 100%, 20px 100%, 0 calc(100% - 20px), 0 20px );
}
```

#### 弹出提示

- transition, transform, filter

```
<div class="cell poptip--right" aria-controls="right">right</div>

<style>
  main {
    width: 100%;
    padding: 99px 69px;
    display: flex;
    flex-wrap: wrap;
  }
  .cell {
    width: 200px;
    height: 52px;
    text-align: center;
    line-height: 52px;
    border-radius: 8px;
    background: #F7F5F1;
    cursor: pointer;
    position: relative;
    border-color: #b4a078;
  }
  .cell[class*=poptip--]::before,
  .cell[class*=poptip--]::after {
    visibility: hidden;
    opacity: 0;
    transform: translate3d(0,0,0);
    transition: all .3s ease .05s;
  }
  .cell[class*=poptip--]:hover::before,
  .cell[class*=poptip--]:hover::after {
    visibility: visible;
    opacity: 1;
  }
  .cell[class*=poptip--right]::before {
    content: '';
    position: absolute;
    width: 0; height: 0;
    border: 6px solid transparent;
    filter: drop-shadow(-1px 0px .5px rgba(180,160,120,.4));
  }
  .cell[class*=poptip--right]::after {
    content: attr(aria-controls);
    position: absolute;
    background: #b4a078;
    font-size: 12px;
    font-weight: normal;
    color: white;
    line-height: 12px;
    padding: 6px 12px;
    white-space: nowrap;
    border-radius: 2px;
    box-shadow: 0px 0px 3px #b4a078;
    filter: drop-shadow(0px 0px 1px rgba(180,160,120,.9));
  }

  .cell[class*=poptip--right]::before {
    border-right-color: inherit;
    top: calc(50% - 6px);
    right: 0;
  }

  .cell[class*=poptip--right]::after {
    top: 50%;
    left: 100%;
    margin-left: -1px;
    transform: translateY(-50%);
  }

  .cell[class*=poptip--right]:hover::before {
    transform: translateX(10px) translateY(0%);
  }

  .cell[class*=poptip--right]:hover::after {
    transform: translateX(10px) translateY(-50%);
  }

</style>

```

#### 多边形

```
#### 梯形
<div class="trapezoid"></div>
.trapezoid {
    width: 80px;
    height: 0;
    border: 40px solid transparent;
    border-top: 0 solid;
    border-bottom: 80px solid #b4a078;
}
#### 五角形
- 原理： 三个梯形组合
<div class="star-5-points"></div>
.star-5-points {
    width: 0;
    height: 0;
    position: relative;
    margin: 50px 0;
    border: 80px solid rgba(0, 0, 0, 0);
    border-top: 0 solid;
    border-bottom: 56px solid #b4a078;
    transform: rotateZ(35deg);
}
.star-5-points::before {
    content: "";
    width: 0;
    height: 0;
    position: absolute;
    top: -36px;
    left: -52px;
    border: 24px solid rgba(0, 0, 0, 0);
    border-top: 0 solid;
    border-bottom: 64px solid #b4a078;
    transform: rotateZ(-35deg);
}
.star-5-points::after {
    content: "";
    width: 0;
    height: 0;
    position: absolute;
    top: 3px;
    left: -86px;
    border: 80px solid rgba(0, 0, 0, 0);
    border-top: 0 solid;
    border-bottom: 56px solid #b4a078;
    transform: rotateZ(-70deg);
}

#### 钻石形
- 原理： 梯形 + 三角形
 .diamond {
      width: 50px;
      height: 0;
      position: relative;
      margin: 20px 0 82px;
      border: 25px solid rgba(0, 0, 0, 0);
      border-top-width: 0;
      border-bottom-color: #b4a078;
 }
.diamond::after {
    content: "";
    width: 0;
    height: 0;
    position: absolute;
    top: 25px;
    left: -25px;
    border: 50px solid rgba(0, 0, 0, 0);
    border-top: 70px solid #b4a078;
    border-bottom-width: 0;
 }
#### 心形
- 原理： 两个带半侧圆矩形的 叠加
.heart {
      content: "";
      display: block;
      width: 100px;
      min-height: 80px;
      position: relative;
      transform-origin: 50% 50% 0;
    }
    .heart:before {
      content: "";
      display: block;
      width: 50px;
      height: 80px;
      position: absolute;
      top: 0;
      left: 50px;
      border-radius: 50px 50px 0 0;
      background: #b4a078;
      transform: rotateZ(-45deg);
      transform-origin: 0 100% 0;
    }
    .heart:after {
      content: "";
      display: block;
      width: 50px;
      height: 80px;
      position: absolute;
      top: 0;
      left: 0;
      border-radius: 50px 50px 0 0;
      background: #b4a078;
      transform: rotateZ(45deg);
      transform-origin: 100% 100% 0;
    }
```
