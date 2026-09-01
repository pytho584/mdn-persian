```markdown
---
title: "Event: stopPropagation() 方法"
short-title: stopPropagation()
slug: Web/API/Event/stopPropagation
page-type: web-api-instance-method
browser-compat: api.Event.stopPropagation
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

**`stopPropagation()`** 方法属于 {{domxref("Event")}} 接口，用于阻止当前事件在捕获和冒泡阶段的进一步传播。但它并不会阻止任何默认行为的发生；例如，链接上的点击仍会被处理。如果您想阻止这些默认行为，请参见 {{domxref("Event.preventDefault", "preventDefault()")}} 方法。此外，它也不会阻止事件传播到当前元素的其他事件处理函数。如果您想阻止这些，请参见 {{domxref("Event.stopImmediatePropagation", "stopImmediatePropagation()")}}。

## 语法

```js-nolint
stopPropagation()
```

### 参数

无。

### 返回值

无。

## 示例

参见 [事件传播](/en-US/docs/Web/API/Document_Object_Model#event_propagation)。
另请参阅 {{domxref("Event.stopImmediatePropagation", "stopImmediatePropagation()")}} 中的示例。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
```