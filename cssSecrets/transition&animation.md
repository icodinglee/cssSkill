#### 输入弹出式提示框

```
 <label>
    <input
        required
        type="text"
        id="username"
        autocomplete="off"
        placeholder="Please input something"
        pattern="^\w+$"/>
    <span class="poptip">Only letters, numbers, and underscore combinations are supported!</span>
</label>

main {
    width: 100%; height: 229px;
    display: flex;
}
label {
    margin: auto;
}
input {
    display: block;
    width: 229px;
    padding: .8em;
    outline: none;
    border: 1px solid #e3e3e3;
    border-radius: 2px;
}
input:focus,input:hover {
    border-color: #b4a078;
}
input:not(:placeholder-shown) {
    border-color: #be4141;
    box-shadow: 0 0 0 2px rgba(255, 100, 97, 0.2);
}
input:not(:placeholder-shown) + .poptip {
    color: #be4141;
}
input:valid {
    border-color: #b4a078;
    box-shadow: 0 0 0 2px rgba(180, 160, 120, 0.2);
}
input:valid + .poptip {
    color: unset;
}
input:not(:focus) + .poptip {
    transform: scale(0);
    animation: elastic-dec .25s;
}

input:focus + .poptip {
    transform: scale(1);
    animation: elastic-grow .45s;
}
.poptip {
    display: inline-block;
    width: 236px;
    font-size: 13px;
    padding: .6em;
    background: #fafafa;
    position: relative;
    margin-left: -3px;
    margin-top: 3px;
    border-radius: 3px;
    filter: drop-shadow(0 0 1px rgba(0, 0, 0, .23456));
    transform-origin: 15px -6px;
}
.poptip::before {
    content: "";
    position: absolute;
    top: -6px; left: 10px;
    border: 9px solid transparent;
    border-bottom-color: #fafafa;
    border-top-width: 0;
}
@keyframes elastic-grow {
    from {
        transform: scale(0);
    }
    70% {
        transform: scale(1.1);
        animation-timing-function: cubic-bezier(.1, .25, .1, .25);
    }
}
@keyframes elastic-dec {
    from {
        transform: scale(1);
    }
    to {
        transform: scale(0);
        animation-timing-function: cubic-bezier(.25, .1, .25, .1);
    }
}

```

#### 打字效果

```
 <span>You-need-to-know-css!</span>
  span {
    display: inline-block;
    width: 21ch;
    font: bold 200% Consolas, Monaco, monospace;   /*Monospaced font*/
    overflow: hidden;
    white-space: nowrap;
    font-weight: 500;
    border-right: 1px solid transparent;
    animation: typing 10s steps(21), caret .5s steps(1) infinite;
  }
  @keyframes typing{
    from {
        width: 0;
    }
  }
  @keyframes caret{
    50% { border-right-color: currentColor}
  }
```
