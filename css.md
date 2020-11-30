# BFC

# 1px 直线

```css
height: 1px;
transform: scale(0.5);
```

# 盒模型的分类

```css
box-sizing: content-box 是W3C盒子模型
box-sizing: border-box 是IE盒子模型
```

# 上中下三栏布局

# 用 css 的方式画一个扇形

clip 使用属性裁切出两个半圆，然后控制这两个半圆的旋转角度，以覆盖底下的圆形，使得图形部分显示。

```css
.pie {
  width: 200px;
  height: 200px;
  border-radius: 200px;
  background-color: deepskyblue;
}

.pie::before {
  content: "";
  width: 200px;
  height: 200px;
  position: absolute;
  background-color: white;
  border-radius: 200px;
  /*裁减半圆，再做旋转*/
  clip: rect(0px, 100px, 200px, 0);
  transform: rotate(-90deg);
}

.pie::after {
  content: "";
  width: 200px;
  height: 200px;
  position: absolute;
  background-color: white;
  border-radius: 200px;
  /*裁减半圆，再做旋转*/
  clip: rect(0px, 200px, 200px, 100px);
  transform: rotate(90deg);
}
```

# sticky footer

```html
<div class="wrapper">
  <div class="content">
    <!-- 页面主体内容区域 -->
  </div>
  <div class="footer">
    <!-- 需要做到 Sticky Footer 效果的页脚 -->
  </div>
</div>
```

absolute 定位 + min-height

```css
html,
body {
  height: 100%;
}

.wrapper {
  position: relative;
  min-height: 100%;
  padding-bottom: 50px;
  box-sizing: border-box;
}

.footer {
  position: absolute;
  bottom: 0;
  height: 50px;
}
```

# `nth-child`和`nth-of-type`的区别

`nth-child` 选择父元素的第 n 个子元素，且该元素类型必须为所指定的类型。

`nth-of-type` 选择父元素中指定类型的子元素中的第 n 个。

html

```html
<div class="parent">
  <h1>test</h1>
  <p>test</p>
  <p>test</p>
</div>
```

css

```css
.parent p:nth-child(2)   /** 匹配第一个P元素 **/
.parent p:nth-of-type(2) /** 匹配第二个P元素 **/
```

# 利用 html css 编写样式，div 垂直 body 居中、div 内的 text 垂直居中，div 高度等于 body 宽度的一半

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      html,
      body {
        margin: 0;
        padding: 0;
      }

      .container {
        position: absolute;
        width: 50vw;
        height: 50vh;
        border: 1px solid red;
        line-height: 50vh;
        top: 50%;
        left: 50%;
        text-align: center;
        transform: translate(-50%, -50%);
      }
    </style>
  </head>
  <body>
    <div class="container">text</div>
  </body>
</html>
```
