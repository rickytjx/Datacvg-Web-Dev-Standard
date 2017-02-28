# HEAD

---

#### 文档类型 {#%E6%96%87%E6%A1%A3%E7%B1%BB%E5%9E%8B}

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明， 这样能够确保在每个浏览器中拥有一致的表现。

```markdown
<!DOCTYPE html>
```

#### 语言属性 {#%E8%AF%AD%E8%A8%80%E5%B1%9E%E6%80%A7}

为什么使用 lang="zh-cmn-Hans" 而不是我们通常写的 lang="zh-CN" 呢? 请参考知乎上的讨论:[网页头部的声明应该是用 lang="zh" 还是 lang="zh-cn"？](http://www.zhihu.com/question/20797118)

```markdown
<!-- 中文 -->
<html lang="zh-Hans">

<!-- 简体中文 -->
<html lang="zh-cmn-Hans">

<!-- 繁体中文 -->
<html lang="zh-cmn-Hant">

<!-- English -->
<html lang="en">
```

#### 字符编码 {#%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81}

* 以无 BOM 的 utf-8 编码作为文件格式;
* 指定字符编码的 meta 必须是 head 的第一个直接子元素；请参考前端观察的博文：[HTML5 Charset 能用吗？](http://www.qianduan.net/html5-charset-can-it.html)

```markdown
<html>
  <head>
    <meta charset="utf-8">
    ......
  </head>
  <body>
    ......
  </body>
</html>
```

#### IE 兼容模式 {#ie-%E5%85%BC%E5%AE%B9%E6%A8%A1%E5%BC%8F}

优先使用最新版本的IE 和 Chrome 内核

```markdown
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
```

#### SEO 优化 {#seo-%E4%BC%98%E5%8C%96}

```markdown
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <!-- SEO -->
  <title>Style Guide</title>
  <meta name="keywords" content="your keywords">
  <meta name="description" content="your description">
  <meta name="author" content="author,email address">
</head>
```

#### viewport {#viewport}

* `viewport`: 一般指的是浏览器窗口内容区的大小，不包含工具条、选项卡等内容；
* `width`: 浏览器宽度，输出设备中的页面可见区域宽度；
* `device-width`: 设备分辨率宽度，输出设备的屏幕可见宽度；
* `initial-scale`: 初始缩放比例；
* `maximum-scale`: 最大缩放比例；

为移动端设备优化，设置可见区域的宽度和初始缩放比例。

```markdown
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### iOS 图标 {#ios-%E5%9B%BE%E6%A0%87}

* apple-touch-icon 图片自动处理成圆角和高光等效果;
* apple-touch-icon-precomposed 禁止系统自动添加效果，直接显示设计原图;

```markdown
<!-- iPhone 和 iTouch，默认 57x57 像素，必须有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

<!-- iPad，72x72 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-72x72-precomposed.png" sizes="72x72">

<!-- Retina iPhone 和 Retina iTouch，114x114 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-114x114-precomposed.png" sizes="114x114">

<!-- Retina iPad，144x144 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-144x144-precomposed.png" sizes="144x144">
```

#### favicon {#favicon}

在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 favicon.ico 。为了保证 favicon 可访问，避免404，必须遵循以下两种方法之一：

* 在 Web Server 根目录放置 favicon.ico 文件；
* 使用 link 指定 favicon；

```markdown
<link rel="shortcut icon" href="path/to/favicon.ico">
```

#### HEAD 模板 {#head-%E6%A8%A1%E6%9D%BF}

```markdown
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <title>Style Guide</title>
  <meta name="description" content="不超过150个字符">
  <meta name="keywords" content="">
  <meta name="author" content="name, email@gmail.com">
  <!-- 为移动设备添加 viewport -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- iOS 图标 -->
  <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">
  <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml" />
  <link rel="shortcut icon" href="path/to/favicon.ico">
</head>
```



