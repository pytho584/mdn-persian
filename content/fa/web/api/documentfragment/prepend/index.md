---
title: "DocumentFragment: prepend() method"
short-title: prepend()
slug: Web/API/DocumentFragment/prepend
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.prepend
---

{{APIRef("DOM")}}

**`DocumentFragment.prepend()`** 方法将一组 {{domxref("Node")}} 对象或字符串插入到文档片段的第一个子节点之前。字符串会作为等效的 {{domxref("Text")}} 节点插入。

此方法会将一个子节点前置到 `DocumentFragment` 中。若要向前置到树中的任意元素，请参阅 {{domxref("Element.prepend()")}}。

## 语法

```js-nolint
prepend(param1)
prepend(param1, param2)
prepend(param1, param2, /* …, */ paramN)
```

### 参数

- `param1`, …, `paramN`
  - : 要插入的一组 {{domxref("Node")}} 对象或字符串。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : 当节点无法插入到层级中的指定位置时抛出。

## 示例

### 将元素前置到文档片段

```js
let fragment = new DocumentFragment();
let div = document.createElement("div");
let p = document.createElement("p");
fragment.append(p);
fragment.prepend(div);

fragment.children; // HTMLCollection [<div>, <p>]
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("DocumentFragment.append()")}}
- {{domxref("Element.prepend()")}}