# 基本规范 {#%E9%80%9A%E7%94%A8%E7%BA%A6%E5%AE%9A}

---

#### 标签 {#%E6%A0%87%E7%AD%BE}

* 自闭合（self-closing）标签，无需闭合 \( 例如：`imginputbrhr`等 \)；
* 可选的闭合标签（closing tag），需闭合 \( 例如：`</li>`或`</body>`\)；
* 尽量减少标签数量；

```markdown
<img src="images/google.png" alt="Google">
<input type="text" name="title">

<ul>
  <li>Style</li>
  <li>Guide</li>
</ul>

<!-- Not recommended -->
<span class="avatar">
  <img src="...">
</span>

<!-- Recommended -->
<img class="avatar" src="...">
```

#### Class 与 ID {#class-%E4%B8%8E-id}

* class 应以功能或内容命名，不以表现形式命名；
* class 与 id 单词字母小写，多个单词组成时，采用中划线`-`分隔；
* 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class；

```markdown
<!-- Not recommended -->
<div class="j-hook left contentWrapper"></div>

<!-- Recommended -->
<div id="j-hook" class="sidebar content-wrapper">
</div>
```

#### 属性顺序 {#%E5%B1%9E%E6%80%A7%E9%A1%BA%E5%BA%8F}

HTML 属性应该按照特定的顺序出现以保证易读性。

* id
* class
* name
* data-xxx
* src, for, type, href
* title, alt
* aria-xxx, role

```markdown
<a id="..." class="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

#### 引号 {#%E5%BC%95%E5%8F%B7}

属性的定义，统一使用双引号。

```markdown
<!-- Not recommended -->
<span id='j-hook' class=text>Google</span>

<!-- Recommended -->
<span id="j-hook" class="text">Google</span>
```

#### 嵌套 {#%E5%B5%8C%E5%A5%97}

`a 不允许嵌套 div`这种约束属于语义嵌套约束，与之区别的约束还有严格嵌套约束，比如`a 不允许嵌套 a`。

严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

**语义嵌套约束**

* `<li>`用于`<ul>`或`<ol>`下；
* `<dd>`,`<dt>`用于`<dl>`下；
* `<thead>`,`<tbody>`,`<tfoot>`,`<tr>`,`<td>`用于`<table>`下；

**严格嵌套约束**

* inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
* `<a>`里不可以嵌套交互式元素`<a>`、`<button>`、`<select>`等;
* `<p>`里不可以嵌套块级元素`<div>`、`<h1>~<h6>`、`<p>`、`<ul>/<ol>/<li>`、`<dl>/<dt>/<dd>`、`<form>`等。

更多详情，参考[WEB标准系列-HTML元素嵌套](http://www.smallni.com/element-nesting/)

#### 布尔值属性 {#%E5%B8%83%E5%B0%94%E5%80%BC%E5%B1%9E%E6%80%A7}

HTML5 规范中`disabled`、`checked`、`selected`等属性不用设置值。

```markdown
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```



