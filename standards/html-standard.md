Html 规范
==================

## 文件格式
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company_logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```
* 在每个 HTML 页面开头使用这个简单地 doctype 来启用标准模式，使其每个浏览器中尽可能一致的展现
* 缩进统一用两个空格(spaces2)
* 属性上，使用双引号，不要使用单引号
* class命名全部小写，单词间使用中划线("-")分隔
* 图片命名全部小写，单词间使用下划线("_")分隔
* 字符编码通常是UTF-8

## 元素语义化
根据元素（有时被错误地称作“标签”）其被创造出来时的初始意义来使用它。打个比方，用 heading 元素来定义头部标题，p 元素来定义文字段落，用 a 元素来定义链接锚点，等等。

不推荐

```html
<b>My page title</b>
<div class="top-navigation">
  <div class="nav-item"><a href="#home">Home</a></div>
  <div class="nav-item"><a href="#news">News</a></div>
  <div class="nav-item"><a href="#about">About</a></div>
</div>
 
<div class="news-page">
  <div class="page-section news">
    <div class="title">All news articles</div>
    <div class="news-article">
      <h2>Bad article</h2>
      <div class="intro">Introduction sub-title</div>
      <div class="content">This is a very bad example for HTML semantics</div>
      <div class="article-side-notes">I think I'm more on the side and should not receive the main credits</div>
      <div class="article-foot-notes">
        This article was created by David <div class="time">2014-01-01 00:00</div>
      </div>
    </div>
 
    <div class="section-footer">
      Related sections: Events, Public holidays
    </div>
  </div>
</div>
```
推荐  

```html
<header>
  <h1>My page title</h1>
</header>
 
<nav class="top-navigation">
  <ul>
    <li class="nav-item"><a href="#home">Home</a></li>
    <li class="nav-item"><a href="#news">News</a></li>
    <li class="nav-item"><a href="#about">About</a></li>
  </ul>
</nav>
 
<main class="news-page" role="main">
  <section class="page-section news">
    <header>
      <h2 class="title">All news articles</h2>
    </header>
 
    <article class="news-article">
      <header>
        <div class="article-title">Good article</div>
        <small class="intro">Introduction sub-title</small>
      </header>
 
      <div class="content">
        <p>This is a good example for HTML semantics</p>
      </div>
      <aside class="article-side-notes">
        <p>I think I'm more on the side and should not receive the main credits</p>
      </aside>
      <footer class="article-foot-notes">
        <p>This article was created by David <time datetime="2014-01-01 00:00" class="time">1 month ago</time></p>
      </footer>
    </article>
 
    <footer class="section-footer">
      <p>Related sections: Events, Public holidays</p>
    </footer>
  </section>
</main>
 
<!-- Your page footer should go into a global footer element -->
<footer class="page-footer">
  Copyright 2014
</footer>
```

## 属性顺序
```html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```
* HTML 属性应该按照特定的顺序出现以保证易读性
* Classes 是为高可复用组件设计的，所以他们处在第一位。Ids 更加具体而且应该尽量少使用（例如, 页内书签），所以他们处在第二位

## 减少标签数量

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```
在编写HTML代码时，需要尽量避免多余的父节点。很多时候，需要通过迭代和重构来使 HTML 变得更少

[更多规范](http://124.160.104.74:5000/)