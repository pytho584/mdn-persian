---
title: "HTMLElement: hidePopover() method"
---

---
title: "HTMLElement: hidePopover() method"
short-title: hidePopover()
slug: Web/API/HTMLElement/hidePopover
page-type: web-api-instance-method
browser-compat: api.HTMLElement.hidePopover
---

{{APIRef("Popover API")}}

`HTMLElement` 接口中的 **`hidePopover()`** 方法会将一个 [popover](/en-US/docs/Web/API/Popover_API) 元素（即带有有效 [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) 属性的元素）从 {{glossary("top layer")}} 中移除，并对其应用 `display: none` 样式，从而将其隐藏。

当对一个正在显示且具有 [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) 属性的元素调用 `hidePopover()` 时，会先触发 {{domxref("HTMLElement/beforetoggle_event", "beforetoggle")}} 事件，接着 popover 被隐藏，随后触发 {{domxref("HTMLElement/toggle_event", "toggle")}} 事件。

## 语法

```js-nolint
hidePopover()
```

### 参数

无。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- `InvalidStateError` {{domxref("DOMException")}}
  - : 如果在另一个 popover 已经在显示或隐藏过程中时调用此方法，则抛出该异常。

## 示例

### 隐藏一个 popover

以下示例实现了通过按下键盘上的特定按键来隐藏 popover 的功能。

#### HTML

```html
<button popovertarget="mypopover">Toggle popover's display</button>
<div id="mypopover" popover="manual">
  You can press <kbd>h</kbd> on your keyboard to close the popover.
</div>
```

#### JavaScript

```js
const popover = document.getElementById("mypopover");

document.addEventListener("keydown", (event) => {
  if (event.key === "h") {
    popover.hidePopover();
  }
});
```

#### 结果

{{EmbedLiveSample("Hiding a popover","100%",100)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Popover API](/en-US/docs/Web/API/Popover_API)