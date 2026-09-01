---
title: "Document: hasFocus() method"
short-title: hasFocus()
slug: Web/API/Document/hasFocus
page-type: web-api-instance-method
browser-compat: api.Document.hasFocus
---

{{APIRef("DOM")}}

{{domxref("Document")}} 接口的 **`hasFocus()`** 方法返回一个布尔值，指示文档或文档内的任何元素是否具有焦点。此方法可用于确定文档中的活动元素是否具有焦点。

> [!NOTE]
> 查看文档时，具有焦点的元素始终是文档中的[活动元素](/en-US/docs/Web/API/Document/activeElement)，但活动元素不一定具有焦点。例如，非前台弹出窗口中的活动元素不具有焦点。

## 语法

```js-nolint
hasFocus()
```

### 参数

无。

### 返回值

如果文档中的活动元素没有焦点，则返回 `false`；如果文档中的活动元素具有焦点，则返回 `true`。

## 示例

### 检查文档是否具有焦点

以下示例检查文档是否具有焦点。名为 `checkPageFocus()` 的函数会根据 `document.hasFocus()` 的结果来更新一个段落元素。打开新窗口会导致文档失去焦点，而切换回原始窗口会使文档重新获得焦点。

```html live-sample___has-focus
<p id="log">Focus check results are shown here.</p>
<button id="newWindow">Open new window</button>
```

```css hidden live-sample___has-focus
body {
  padding: 1rem;
  background: gray;
  text-align: center;
  font: 1.5rem sans-serif;
}
```

```js live-sample___has-focus
const body = document.querySelector("body");
const log = document.getElementById("log");

function checkDocumentFocus() {
  if (document.hasFocus()) {
    log.textContent = "This document has focus.";
    body.style.background = "white";
  } else {
    log.textContent = "This document does not have focus.";
    body.style.background = "gray";
  }
}

function openWindow() {
  window.open(
    "https://developer.mozilla.org/",
    "MDN",
    "width=640,height=320,left=150,top=150",
  );
}

document.getElementById("newWindow").addEventListener("click", openWindow);
setInterval(checkDocumentFocus, 300);
```

{{EmbedLiveSample('has-focus', , , , , , , 'allow-popups')}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Document.activeElement")}}
- [使用页面可见性 API](/en-US/docs/Web/API/Page_Visibility_API)