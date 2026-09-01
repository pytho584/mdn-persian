---
title: "Element: closest() method"
short-title: closest()
slug: Web/API/Element/closest
page-type: web-api-instance-method
browser-compat: api.Element.closest
---

{{APIRef("DOM")}}

**`closest()`** 方法属于 {{domxref("Element")}} 接口，它会遍历该元素及其父元素（朝着文档根节点方向），直到找到一个与指定的 [CSS 选择器](/en-US/docs/Learn_web_development/Core/Styling_basics/Basic_selectors)匹配的节点。

## 语法

```js-nolint
closest(selectors)
```

### 参数

- `selectors`
  - : 一个包含有效 [CSS 选择器](/en-US/docs/Learn_web_development/Core/Styling_basics/Basic_selectors)的字符串，用于与 {{domxref("Element")}} 及其祖先进行匹配。

### 返回值

返回与 `selectors` 匹配的最近祖先 {{domxref("Element")}} 或元素自身。如果不存在这样的元素，则返回 `null`。

### 异常

- `SyntaxError` {{domxref("DOMException")}}
  - : 如果 `selectors` 不是有效的 CSS 选择器，则抛出该错误。

## 示例

### HTML

```html
<article>
  <div id="div-01">
    Here is div-01
    <div id="div-02">
      Here is div-02
      <div id="div-03">Here is div-03</div>
    </div>
  </div>
</article>
```

### JavaScript

```js
const el = document.getElementById("div-03");

// the closest ancestor with the id of "div-02"
console.log(el.closest("#div-02")); // <div id="div-02">

// the closest ancestor which is a div in a div
console.log(el.closest("div div")); // <div id="div-03">

// the closest ancestor which is a div and has a parent article
console.log(el.closest("article > div")); // <div id="div-01">

// the closest ancestor which is not a div
console.log(el.closest(":not(div)")); // <article>
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

### 兼容性说明

- 在 Edge 15–18 中，如果元素尚未（直接或间接）连接到上下文对象（例如常规 DOM 中的 {{domxref("Document")}} 对象），`document.createElement(tagName).closest(tagName)` 将返回 `null`。

## 参见

- [CSS 选择器](/en-US/docs/Web/CSS/Guides/Selectors) 模块
- 其他接受选择器的 {{domxref("Element")}} 方法：{{domxref("Element.querySelector()")}}、{{domxref("Element.querySelectorAll()")}} 和 {{domxref("Element.matches()")}}。