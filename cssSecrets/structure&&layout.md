#### 粘性 footer

如果页面内容不够的话，footer 贴附在 viewport 底部，如果页面内容够的话，footer 位于内容底部

```
<main class="main">
    <header>
      <h1>Site Header</h1>
    </header>
    <section>
      <input id="con-1" type="checkbox" checked/>
      <label for="con-1"><b>Toggle contents</b></label>
      <p>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
        1 <br/>
      </p>
    </section>
    <footer>
      <p>© 2018 LHammer</p>
      <p>CSS Tricks need to know for web developer.</p>
    </footer>
  </main>
  main{
    width: 100%; height: 392px;
  }
  section input:checked ~ p{
    display: none
  }
  .main > header,
  .main > section,
  .main > footer{
    padding: .1em calc(50% - 329px);
    text-align: justify;
    hyphens: auto;
  }
  header{
    text-align: center;
  }
  section {
    box-sizing: border-box;
    min-height: calc(100% - 59px - 107px);
  }
  footer{
    color: white;
    background: #747e7f;
  }
```

##### 居中大法 - 推荐使用

```
第一种： flex + margin: auto
main{
    width: 100%;
    min-height: 152px;
    display: flex;
}
main > span {
    background: #b4a078;
    color: white;
    margin: auto;
    padding: .3em 1em .5em;
    border-radius: 3px;
    box-shadow: 0 0 .5em #b4a078;
}

第二种： display: grid
 main{
    width: 100%;
    min-height: 152px;
    display: grid;
    justify-content: center;
    align-items: center;
}
main > span {
    background: #b4a078;
    color: white;
    padding: .3em 1em .5em;
    border-radius: 3px;
    box-shadow: 0 0 .5em #b4a078;
}

第三种：position: absolute + translate
main{
    width: 100%;
    min-height: 152px;
    display: flex;
}
main > span {
    position: absolute;
    top: 50%; left: 50%;
    background: #b4a078;
    color: white;
    padding: .3em 1em .5em;
    border-radius: 3px;
    box-shadow: 0 0 .5em #b4a078;
    transform: translate(-50%, -50%);
}

第四种： display: table/table-cell + vertical-align: middle
<main>
    <div><span>Center me, please!</span></div>
</main>
main {
    width: 100%;
    height: 152px;
    display: table;
}
main > div {
    display: table-cell;
    text-align: center;
    vertical-align: middle;
}
main > div > span {
    width: 50%;
    background: #b4a078;
    color: white;
    padding: .3em 1em .5em;
    border-radius: 3px;
    box-shadow: 0 0 .5em #b4a078;
}
```

##### 左中右布局， 左侧高度变化， 右侧内容需随之自适应

```
<main class="main">
    <section>
      <span class="left">
        <div>
          这是左边不断变化的内容
        </div>
      </span>
      <span class="center">Vertical centering<br>Vertical centering Vertical centering</span>
      <span class="right">Vertical centering</span>
    </section>
  </main>

main {
    width: 100%;
    padding: 39px 29px;
    font-size: 12px;
}
section {
    width: 100%;
    box-shadow: 0 0 0 1px #eee;
    overflow: hidden;
}
section > span{
    width: 20%;
    display: inline-block;
    vertical-align: middle;
    margin-left: -3px;
    padding-left: 12px;
    text-align: center
}
section::after {
    content: '';
    display: inline-block;
    height: 100%;
    vertical-align: middle;
}
.left {
    width: 45%;
    margin-left: 0;
    padding: 12px;
}
.center {
    width: 35%;
    border: 1px solid #eee;
    padding-top: 999px;       /* h */
    padding-bottom: 999px;    /* a */
    margin-top: -999px;       /* c */
    margin-bottom: -999px;    /* k */
    position: relative;
}
.left .item {
    width: 100%; height: 85px;
    text-align: center;
    line-height: 85px;
    background: rgba(180,160,120,.1);
    position: relative;
}
.left .item:not(:first-child) {
    margin-top: 24px;
}
.left .item:not(:first-child)::before {
    content: '';
    position: absolute;
    top: -12px; right: -12px; left: -12px;
    border-top: 1px solid #eee;
}
```
