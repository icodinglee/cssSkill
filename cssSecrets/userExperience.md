#### 自定义 checkbox

#### 自定义 radio

#### 自定义 switch

#### 自定义输入框

```
 <input type="text" placeholder="Please type phone number or name">
  ::-webkit-input-placeholder {
    line-height: 1.375em;
  }
  input {
    outline: none;
    color: #666;
    font-size: .9em;
    padding: .5em;
    border-radius: .2em;
    border: 1px solid #e3e3e3;
    -webkit-appearance: none;
  }
  input:hover {
    border: 1px solid #b4a078;
  }
  input:focus {
    border: 1px solid #b4a078;
    box-shadow: 0 0 0 2px rgba(180, 160, 120, 0.2);
  }
```

##### 使用 box-shadow 实现遮罩

```
 dialog{
    width: 400px; height: 120px;
    text-align: center;
    line-height: 84px;
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    box-shadow: 0 .1em .2em rgba(0,0,0,.5), 0 0 0 50vmax rgba(0,0,0,.3);
    z-index: 99;
  }
```

##### 文本下划线

```
<main>
    <p><a>please add beauuuuuuuutiful underline effect!</a></p>
</main>

// 使用 box-shadow
main {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 39px 0;
    user-select: none;
    font: 16px / 1 Helvetica, sans-serif;
}
p > a {
    box-shadow: 0 -1px 0px 0 #b4a078 inset;
}

// 使用after
p > a {
    position: relative;
}
p > a:after {
    content: '';
    width: 100%;
    position: absolute;
    bottom: 0; right: 0; left: 0;
    border-bottom: 1px solid #b4a078;
}
<p><a>Please add beauuuuuuuutiful underline effect</a></p>

// 使用linear-gradient 【推荐使用】
p > a {
    padding-bottom: 1px;
    background: linear-gradient(#b4a078, #b4a078) no-repeat;
    background-size: 100% 1px;
    background-position: 0 18px;
}
p > a:hover{
    animation: text-underline-slideInLeft 1.2s linear infinite forwards;
}
@keyframes text-underline-slideInLeft {
    from {
      background-position-x: -432px;
    }
    50% {
      background-position-x: 0;
    }
    to {
      background-position-x: 432px;
    }
}

// 绘制虚线
p > a {
    background: linear-gradient(90deg, #b4a078 66%, transparent 0) repeat-x;
    background-size: .3em 1px;
    background-position: 0 1em;
}
```
