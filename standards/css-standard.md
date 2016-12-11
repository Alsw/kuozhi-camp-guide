CSS 规范
==================

## 文件格式
* 缩进统一用两个空格(spaces2)

## 语法
```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0px 1px 2px #ccc, inset 0 1px 0 #fff;
}
```
* 使用组合选择器时，保持每个独立的选择器占用一行
* 为了代码的易读性，在每个声明的左括号前增加一个空格
* 声明块的右括号应该另起一行
* 每条声明<code> :</code>后应该插入一个空格
* 每条声明应该只占用一行来保证错误报告更加准确
* 不要在颜色值 rgb(), rgba(), hsl(), hsla(), 和 rect() 中增加空格
* 所有的十六进制值都应该使用小写字母，例如 #fff。因为小写字母有更多样的外形，在浏览文档时，他们能够更轻松的被区分开来
* 不要为 0 指明单位，比如使用 <code>margin: 0; </code>而不是 <code>margin: 0px;</code>

## 声明顺序
```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```
相关的属性声明应该以下面的顺序分组处理  
1. Positioning  
2. Box model 盒模型  
3. Typographic 排版  
4. Visual 外观

Positioning 处在第一位，因为他可以使一个元素脱离正常文本流，并且覆盖盒模型相关的样式。盒模型紧跟其后，因为他决定了一个组件的大小和位置。

其他属性只在组件内部起作用或者不会对前面两种情况的结果产生影响，所以他们排在后面

## 属性简写

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

/* Good example */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

坚持限制属性取值简写的使用，属性简写需要你必须显式设置所有取值。常见的属性简写滥用包括:  

1. padding
2. margin
3. font
4. background
5. border
6. border-radius


大多数情况下，我们并不需要设置属性简写中包含的所有值。例如，HTML 头部只设置上下的 margin，所以如果需要，只设置这两个值。过度使用属性简写往往会导致更混乱的代码，其中包含不必要的重写和意想不到的副作用

## LESS

```less
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}
```
EduSoho采用LESS预处理语言来书写CSS

避免不必要的嵌套。可以进行嵌套，不意味着你应该这样做。只有在需要给父元素增加样式并且同时存在多个子元素时才需要考虑嵌套

一般LESS嵌套不要超过3层

以组件为单位组织代码

## Class 命名
```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

保持 Class 命名为全小写，可以使用短划线（不要使用下划线和 camelCase 命名）。短划线应该作为相关类的自然间断。(例如，<code>.btn</code> 和 <code>.btn-danger</code>)

避免过度使用简写。<code>.btn</code> 可以很好地描述 button，但是 .s 不能代表任何元素

Class 的命名应该尽量短，也要尽量明确

使用有意义的名称；使用结构化或者作用目标相关，而不是抽象的名称

命名时使用最近的父节点或者父 class 作为前缀

使用 <code>.js-*</code> classes 来表示行为(相对于样式)，但是不要在 CSS 中定义这些 classes


## 选择器

```css
/* Bad example */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
#content .title {...}

/* Good example */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
.content .title {...}
```

使用 classes 而不是通用元素标签来优化渲染性能

一般情况下ID不应该被应用于样式

避免在经常出现的组件中使用一些属性选择器 (例如，<code>[class^="..."]</code>)。浏览器性能会受到这些情况的影响

减少选择器的长度，每个组合选择器选择器的条目应该尽量控制在 3 个以内

只在必要的情况下使用后代选择器 (例如，没有使用带前缀 classes 的情况)

CSS选择器中避免标签名,从分离的角度考虑,在表现层中不应该分配html标记/语义

[更多规范](http://124.160.104.74:5000/)