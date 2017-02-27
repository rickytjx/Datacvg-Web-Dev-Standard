# 通用规范 {#%E9%80%9A%E7%94%A8%E7%BA%A6%E5%AE%9A}

---

#### 代码组织 {#%E4%BB%A3%E7%A0%81%E7%BB%84%E7%BB%87}

* 以组件为单位组织代码段；
* 制定一致的注释规范；
* `组件块和子组件块`以及`声明块`之间使用**一空行**分隔，`子组件块`之间**三空行**分隔；
* 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动；

良好的注释是非常重要的。请留出时间来描述组件（component）的工作方式、局限性和构建它们的方法。不要让你的团队其它成员 来猜测一段不通用或不明显的代码的目的。

提示：通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。

```css
/* ==========================================================================
   组件块
 ============================================================================ */
/* 子组件块
 ============================================================================ */
.selector {
  padding:15px;
  margin-bottom:15px;
}


/* 子组件块 
 ============================================================================ */
.selector-secondary {
  display: block; /* 注释*/
}

.selector-three {
  display: span;
}
```

#### Class 和 ID {#class-%E5%92%8C-id}

* 使用语义化、通用的命名方式；
* 使用连字符 - 作为 ID、Class 名称界定符，不要驼峰命名法和下划线；
* 避免选择器嵌套层级过多，尽量少于 3 级；
* 避免选择器和 Class、ID 叠加使用；

出于[性能考量](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/)，在没有必要的情况下避免元素选择器叠加 Class、ID 使用。

元素选择器和 ID、Class 混合使用也违反关注分离原则。如果HTML标签修改了，就要再去修改 CSS 代码，不利于后期维护。

```css
/* Not recommended */
.red {}
.box_green {}
.page .header .login #username input {}
ul#example {}

/* Recommended */
#nav {}
.box-video {}
#username input {}
#example {}
```

#### 声明块格式 {#%E5%A3%B0%E6%98%8E%E5%9D%97%E6%A0%BC%E5%BC%8F}

* 选择器分组时，保持独立的选择器占用一行；
* 声明块的左括号`{`前添加一个空格；
* 声明块的右括号`}`应单独成行；
* 声明语句中的`:`后应添加一个空格；
* 声明语句应以分号`;`结尾；
* 一般以逗号分隔的属性值，每个逗号后应添加一个空格；
* `rgb()`、`rgba()`、`hsl()`、`hsla()`或`rect()`括号内的值，逗号分隔，但逗号后不添加一个空格；
* 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，`.5`代替`0.5`；`-.5px`代替`-0.5px`）；
* 十六进制值应该全部小写和尽量简写，例如，`#fff`代替`#ffffff`；
* 避免为 0 值指定单位，例如，用`margin: 0;`代替`margin: 0px;`；

```css
/*  Not recommended  */
.selector, .selector-secondary, .selector[type=text] {
  padding: 15px;
  margin: 0px 0px 15px;
  background-color: rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC, inset 0 1px 0 #FFFFFF;
}


/* Recommended */
.selector,
.selector-secondary,
.selector[type="text"]{
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0, 0, 0, .5);
  box-shadow:0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

#### 声明顺序 {#%E5%A3%B0%E6%98%8E%E9%A1%BA%E5%BA%8F}

相关属性应为一组，推荐的样式编写顺序

1. Positioning
2. Box model
3. Typographic
4. Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型决定了组件的尺寸和位置，因此排在第二位。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box model */
  display: block;
  box-sizing: border-box;
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 1px solid #e5e5e5;
  border-radius: 3px;
  margin: 10px;
  float: right;
  overflow: hidden;

  /* Typographic */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  color: #fff;
  opacity: .8;

  /* Other */
  cursor: pointer;
}
```

#### 引号使用 {#%E5%BC%95%E5%8F%B7%E4%BD%BF%E7%94%A8}

`url()`、属性选择符、属性值使用双引号。 参考[Is quoting the value of url\(\) really necessary?](http://stackoverflow.com/questions/2168855/is-quoting-the-value-of-url-really-necessary)

```css
/* Not recommended */
@import url(//www.google.com/css/maia.css);

html {
  font-family: 'open sans', arial, sans-serif;
}

/* Recommended */
@import url("//www.google.com/css/maia.css");

html{
  font-family: "open sans", arial, sans-serif;
}

.selector[type="text"]{

}
```

#### 媒体查询（Media query）的位置 {#%E5%AA%92%E4%BD%93%E6%9F%A5%E8%AF%A2%EF%BC%88media-query%EF%BC%89%E7%9A%84%E4%BD%8D%E7%BD%AE}

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (max-width: 768px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}

```

#### 不要使用`@import` {#%E4%B8%8D%E8%A6%81%E4%BD%BF%E7%94%A8-import}

与`<link>`相比，`@import`要慢很多，不光增加额外的请求数，还会导致不可预料的问题。

替代办法：

* 使用多个元素；
* 通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件；
* 其他 CSS 文件合并工具；

参考[don’t use @import](http://www.stevesouders.com/blog/2009/04/09/dont-use-import/)；

#### 链接的样式顺序： {#%E9%93%BE%E6%8E%A5%E7%9A%84%E6%A0%B7%E5%BC%8F%E9%A1%BA%E5%BA%8F%EF%BC%9A}

`a:link -> a:visited -> a:hover -> a:active（LoVeHAte）`

#### 无需添加浏览器厂商前缀 {#%E6%97%A0%E9%9C%80%E6%B7%BB%E5%8A%A0%E6%B5%8F%E8%A7%88%E5%99%A8%E5%8E%82%E5%95%86%E5%89%8D%E7%BC%80}

使用[Autoprefixer](https://github.com/postcss/autoprefixer)自动添加浏览器厂商前缀，编写 CSS 时不需要添加浏览器前缀，直接使用标准的 CSS 编写。

Autoprefixer 通过[Can I use](http://caniuse.com/)，按兼容的要求，对相应的 CSS 代码添加浏览器厂商前缀。

