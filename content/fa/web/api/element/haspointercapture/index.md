---
title: "Element: hasPointerCapture() method"
---

---
title: "Element: hasPointerCapture() method"
short-title: hasPointerCapture()
slug: Web/API/Element/hasPointerCapture
page-type: web-api-instance-method
browser-compat: api.Element.hasPointerCapture
---

{{APIRef("DOM")}}

**`hasPointerCapture()`** 是 {{domxref("Element")}} 接口的一个方法，用于检查调用该方法的元素是否对给定指针 ID 所标识的指针启用了[指针捕获](/en-US/docs/Web/API/Pointer_events#pointer_capture)。

## 语法

```js-nolint
hasPointerCapture(pointerId)
```

### 参数

- `pointerId`
  - : {{domxref("PointerEvent")}} 对象的 {{domxref("PointerEvent.pointerId", "pointerId")}} 属性值。

### 返回值

一个布尔值——如果该元素对给定指针 ID 标识的指针具有指针捕获，则为 `true`；否则为 `false`。

## 示例

```html
<div id="target">Touch this element with a pointer.</div>
```

```js
const el = document.getElementById("target");
el.addEventListener("pointerdown", (ev) => {
  // Element 'target' will receive/capture further events
  el.setPointerCapture(ev.pointerId);

  // …

  // Check whether element still has pointer capture
  const pointerCap = el.hasPointerCapture(ev.pointerId);
  if (pointerCap) {
    // We've still got pointer capture
  } else {
    // oops, we've lost pointer capture!
  }
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{ domxref("Element.setPointerCapture()")}}
- {{ domxref("Element.releasePointerCapture()")}}
- {{ domxref("Pointer_events","Pointer Events", "", 1) }}