---
title: "HTMLImageElement: srcset property"
short-title: srcset
slug: Web/API/HTMLImageElement/srcset
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.srcset
---

{{APIRef("HTML DOM")}}

**`srcset`** 属性属于 {{domxref("HTMLImageElement")}} 接口，它标识一个或多个 *图像候选字符串*，这些字符串以逗号（`,`）分隔，每个字符串指定在特定情况下要使用的图像资源。每个图像候选字符串包含一个图像 URL 以及一个可选的宽度或像素密度描述符，该描述符指示在何种情况下应使用该候选图像，而不是使用由 {{domxref("HTMLImageElement.src", "src")}} 属性指定的图像。它反映了 `<img>` 元素的 [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) 内容属性。

`srcset` 属性与 {{domxref("HTMLImageElement.sizes", "sizes")}} 属性一同构成了响应式网站设计的关键组成部分，因为它们可以结合使用，使页面根据渲染环境选择合适的图像。

## 值

一个字符串。关于 `srcset` 属性的语法，请参阅 HTML [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) 参考。

## 示例

### 设置 srcset 属性

```js
const img = new Image();
img.srcset =
  "/en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-400px.png 2x, /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-200px.png";
img.alt = "An example picture";
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [HTML 图像](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_images)
- [响应式图像](/en-US/docs/Web/HTML/Guides/Responsive_images)
- [图像文件类型与格式指南](/en-US/docs/Web/Media/Guides/Formats/Image_types)
- {{domxref("HTMLImageElement.currentSrc")}}
- {{domxref("HTMLImageElement.sizes")}}
- {{domxref("HTMLImageElement.src")}}