---
title: "Element: getClientRects() method"
short-title: getClientRects()
slug: Web/API/Element/getClientRects
page-type: web-api-instance-method
browser-compat: api.Element.getClientRects
---

{{APIRef("DOM")}}

**`getClientRects()`** 方法属于 {{domxref("Element")}} 接口，返回一个 {{DOMxRef("DOMRect")}} 对象的集合，这些对象表示客户端中每个 [CSS 边框盒](/en-US/docs/Web/CSS/Guides/Box_model/Introduction) 的边界矩形。

大多数元素只有一个边框盒，但多行的[行内级元素](/en-US/docs/Glossary/Inline-level_content)（例如默认情况下的多行 {{HTMLElement("span")}} 元素）每一行都有一个边框盒。

## 语法

```js-nolint
getClientRects()
```

### 参数

无。

### 返回值

返回值是一个 {{DOMxRef("DOMRect")}} 对象的集合，每个对象对应与该元素关联的一个 CSS 边框盒。每个 {{DOMxRef("DOMRect")}} 对象以像素为单位描述边框盒，其左上角相对于视口的左上角。对于带标题的表格，即使标题位于表格的边框盒之外，也会包含标题。当在外部 `<svg>` 之外的 SVG 元素上调用时，结果矩形所相对的“视口”是该元素的外部 `<svg>` 所建立的视口（需要明确的是，这些矩形也会受到外部 `<svg>` 的 `viewBox` 变换的影响，如果有的话）。

在计算矩形时，会考虑视口区域（或任何其他可滚动元素）已发生的滚动量。

返回的矩形不包含可能溢出的任何子元素的边界。

对于 HTML {{HtmlElement("area")}} 元素、自身不渲染任何内容的 SVG 元素、`display:none` 元素，以及一般任何未直接渲染的元素，将返回空列表。

即使 CSS 盒的边框盒为空，也会返回矩形。`left`、`top`、`right` 和 `bottom` 坐标仍然有意义。

可能存在小数的像素偏移。

## 示例

这些示例以不同颜色绘制客户端矩形。请注意，绘制客户端矩形的 JavaScript 函数通过类名 `withClientRectsOverlay` 与标记连接。

### HTML

示例 1：此 HTML 创建三个段落，每个段落内有一个 `<span>`，并分别嵌入 `<div>` 块中。为第二个块中的段落以及第三个块中的 `<span>` 元素绘制客户端矩形。

```html
<h3>A paragraph with a span inside</h3>
<p>
  Both the span and the paragraph have a border set. The client rects are in
  red. Note that the p has only one border box, while the span has multiple
  border boxes.
</p>

<div>
  <strong>Original</strong>
  <p>
    <span>Paragraph that spans multiple lines</span>
  </p>
</div>

<div>
  <strong>p's rect</strong>
  <p class="withClientRectsOverlay">
    <span>Paragraph that spans multiple lines</span>
  </p>
</div>

<div>
  <strong>span's rect</strong>
  <p>
    <span class="withClientRectsOverlay"
      >Paragraph that spans multiple lines</span
    >
  </p>
</div>
```

示例 2：此 HTML 创建三个有序列表。为第二个块中的 `<ol>` 以及第三个块中的每个 `<li>` 元素绘制客户端矩形。

```html
<h3>A list</h3>
<p>
  Note that the border box doesn't include the number, so neither do the client
  rects.
</p>

<div>
  <strong>Original</strong>
  <ol>
    <li>Item 1</li>
    <li>Item 2</li>
  </ol>
</div>

<div>
  <strong>ol's rect</strong>
  <ol class="withClientRectsOverlay">
    <li>Item 1</li>
    <li>Item 2</li>
  </ol>
</div>

<div>
  <strong>each li's rect</strong>
  <ol>
    <li class="withClientRectsOverlay">Item 1</li>
    <li class="withClientRectsOverlay">Item 2</li>
  </ol>
</div>
```

示例 3：此 HTML 创建两个带标题的表格。为第二个块中的 `<table>` 绘制客户端矩形。

```html
<h3>A table with a caption</h3>
<p>
  Although the table's border box doesn't include the caption, the client rects
  do include the caption.
</p>

<div>
  <strong>Original</strong>
  <table>
    <caption>
      caption
    </caption>
    <thead>
      <tr>
        <th>thead</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>tbody</td>
      </tr>
    </tbody>
  </table>
</div>

<div>
  <strong>table's rect</strong>
  <table class="withClientRectsOverlay">
    <caption>
      caption
    </caption>
    <thead>
      <tr>
        <th>thead</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>tbody</td>
      </tr>
    </tbody>
  </table>
</div>
```

### CSS

CSS 为第一个示例中每个 `<div>` 块内的段落和 `<span>` 绘制边框，为第二个示例中的 `<ol>` 和 `<li>` 绘制边框，并为第三个示例中的 `<table>`、`<th>` 和 `<td>` 元素绘制边框。

```css
strong {
  text-align: center;
}
div {
  display: inline-block;
  width: 150px;
}
div p,
ol,
table {
  border: 1px solid blue;
}
span,
li,
th,
td {
  border: 1px solid green;
}
```

### JavaScript

JavaScript 代码为所有分配了 CSS 类 `withClientRectsOverlay` 的 HTML 元素绘制客户端矩形。

```js
function addClientRectsOverlay(elt) {
  /* Absolutely position a div over each client rect so that its border width
     is the same as the rectangle's width.
     Note: the overlays will be out of place if the user resizes or zooms. */
  const rects = elt.getClientRects();
  for (const rect of rects) {
    const tableRectDiv = document.createElement("div");
    tableRectDiv.style.position = "absolute";
    tableRectDiv.style.border = "1px solid red";
    const scrollTop =
      document.documentElement.scrollTop || document.body.scrollTop;
    const scrollLeft =
      document.documentElement.scrollLeft || document.body.scrollLeft;
    tableRectDiv.style.margin = tableRectDiv.style.padding = "0";
    tableRectDiv.style.top = `${rect.top + scrollTop}px`;
    tableRectDiv.style.left = `${rect.left + scrollLeft}px`;
    // We want rect.width to be the border width, so content width is 2px less.
    tableRectDiv.style.width = `${rect.width - 2}px`;
    tableRectDiv.style.height = `${rect.height - 2}px`;
    document.body.appendChild(tableRectDiv);
  }
}

(() => {
  /* Call function addClientRectsOverlay(elt) for all elements with
     assigned class "withClientRectsOverlay" */
  const elems = document.getElementsByClassName("withClientRectsOverlay");
  for (const elem of elems) {
    addClientRectsOverlay(elem);
  }
})();
```

### 结果

{{EmbedLiveSample('Examples', 680, 650)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{DOMxRef("Element.getBoundingClientRect()")}}