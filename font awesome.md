# Font Awesome 图标

Font Awesome 是一套绝佳的图标字体库和CSS框架。

Font Awesome 字体为您提供可缩放矢量图标,它可以被定制大小、颜色、阴影以及任何可以用CSS的样式。

要使用Font Awesome图标，请在HTML页面的 部分中添加以下行：

1、国内推荐 CDN：

```css
<link rel="stylesheet" href="https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css">
```

2、海外推荐 CDN

```css
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
```

您可以使用前缀 **fa** 和图标的名称来放置 Font Awesome 图标。

## 实例

```html
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" href="https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css">
</head>
<body>
 
<i class="fa fa-car"></i>
<i class="fa fa-car" style="font-size:48px;"></i>
<i class="fa fa-car" style="font-size:60px;color:red;"></i>
 
</body>
</html>
```

Font Awesome 设计为与内联元素一起使用。 <i>和 <span> 元素广泛用于图标。

另外注意，如果更改图标容器的字体大小或颜色，图标会更改。

## 大图标

fa-lg (增加33％)，fa-2x，fa-3x， fa-4x，或 fa-5x 类用于增加相对于其容器的图标大小。

```html
<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" href="https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css">
</head>
<body>
 
<i class="fa fa-car fa-lg"></i>
<i class="fa fa-car fa-2x"></i>
<i class="fa fa-car fa-3x"></i>
<i class="fa fa-car fa-4x"></i>
<i class="fa fa-car fa-5x"></i>
 
</body>
</html>
```

## 列表图标

fa-ul 和 fa-li 类用于替换无序列表中的默认前缀。

```html
<ul class="fa-ul">
  <li><i class="fa-li fa fa-check-square"></i>List icons</li>
  <li><i class="fa-li fa fa-spinner fa-spin"></i>List icons</li>
  <li><i class="fa-li fa fa-square"></i>List icons</li>
</ul>
```

## 动态图标

fa-spin 类可以让图标旋转, fa-pulse 类可以使图标以 8 步为周期进行旋转。

```html
<i class="fa fa-spinner fa-spin"></i>
<i class="fa fa-circle-o-notch fa-spin"></i>
<i class="fa fa-refresh fa-spin"></i>
<i class="fa fa-cog fa-spin"></i>
<i class="fa fa-spinner fa-pulse"></i>
```

## 旋转和翻转的图标

fa-rotate-* 和 fa-flip-* 类用于旋转和翻转图标。

```html
<i class="fa fa-shield"></i>
<i class="fa fa-shield fa-rotate-90"></i>
<i class="fa fa-shield fa-rotate-180"></i>
<i class="fa fa-shield fa-rotate-270"></i>
<i class="fa fa-shield fa-flip-horizontal"></i>
<i class="fa fa-shield fa-flip-vertical"></i>
```

等等......