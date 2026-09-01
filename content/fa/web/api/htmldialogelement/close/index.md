---
title: "HTMLDialogElement: close() method"
short-title: close()
slug: Web/API/HTMLDialogElement/close
page-type: web-api-instance-method
browser-compat: api.HTMLDialogElement.close
---

{{ APIRef("HTML DOM") }}

**`close()`** 方法属于 {{domxref("HTMLDialogElement")}} 接口，用于关闭 {{htmlelement("dialog")}} 元素。可以传入一个可选字符串作为参数，用于更新对话框的 {{domxref("HTMLDialogElement.returnValue", "returnValue")}}。

对话框关闭后会触发 {{domxref("HTMLDialogElement.close_event", "close")}} 事件。与调用 {{domxref("HTMLDialogElement.requestClose()")}} 不同，`close()` 的关闭操作无法被取消。

## 语法

```js-nolint
close()
close(returnValue)
```

### 参数

- `returnValue` {{optional_inline}}
  - : 一个字符串，用于替换 {{domxref("HTMLDialogElement.returnValue")}} 中已有的值。

### 返回值

无（{{jsxref("undefined")}}）。

## 示例

### 关闭一个对话框

以下示例展示了一个按钮，点击后会通过 {{domxref("HTMLDialogElement.showModal()", "showModal()")}} 方法打开一个 {{htmlelement("dialog")}}。之后你可以点击 _Close_ 按钮（使用 `close()` 方法）来关闭对话框。

_Close_ 按钮关闭对话框时不传入 {{domxref("HTMLDialogElement.returnValue", "returnValue")}}，而 _Close w/ return value_ 按钮关闭对话框时会传入一个 {{domxref("HTMLDialogElement.returnValue", "returnValue")}}。

#### HTML

```html
<dialog id="dialog">
  <button type="button" id="close">Close</button>
  <button type="button" id="close-w-value">Close w/ return value</button>
</dialog>

<button id="open">Open dialog</button>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 170px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

```js hidden
const logElement = document.getElementById("log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const closeButton = document.getElementById("close");
const closeWithValueButton = document.getElementById("close-w-value");

// Update button opens a modal dialog
openButton.addEventListener("click", () => {
  // Reset the return value
  dialog.returnValue = "";
  // Show the dialog
  dialog.showModal();
});

// Close button closes the dialog box
closeButton.addEventListener("click", () => {
  dialog.close();
});

// Close button closes the dialog box with a return value
closeWithValueButton.addEventListener("click", () => {
  dialog.close(`Closed at ${new Date().toLocaleTimeString()}`);
});

// Form close button closes the dialog box
dialog.addEventListener("close", () => {
  log(`Dialog closed. Return value: "${dialog.returnValue}"`);
});
```

> [!NOTE]
>
> 需要注意的是，你也可以通过提交一个带有 [`method="dialog"`](/en-US/docs/Web/HTML/Reference/Elements/form#method) 属性的 {{htmlelement("form")}} 元素来自动关闭 `<dialog>`。

### 结果

{{ EmbedLiveSample('Closing a dialog', '100%', '250px') }}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- HTML {{htmlelement("dialog")}} 元素
- {{domxref("HTMLDialogElement.close_event", "close")}} 事件
- {{domxref("HTMLDialogElement.requestClose()")}}