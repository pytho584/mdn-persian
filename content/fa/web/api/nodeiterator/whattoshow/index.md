---
title: "NodeIterator: whatToShow property"
short-title: whatToShow
slug: Web/API/NodeIterator/whatToShow
page-type: web-api-instance-property
browser-compat: api.NodeIterator.whatToShow
---

{{APIRef("DOM")}}

**`NodeIterator.whatToShow`** 只读属性表示一个 `unsigned integer`（无符号整数），该整数是一个位掩码，指示 {{domxref("NodeIterator")}} 应返回哪些类型的节点。

## 值

一个非负整数。有关可能值的列表，请参阅 [`document.createNodeIterator()`](/en-US/docs/Web/API/Document/createNodeIterator#whattoshow)。

## 示例

```js
const nodeIterator = document.createNodeIterator(
  document.body,
  NodeFilter.SHOW_ELEMENT | NodeFilter.SHOW_COMMENT | NodeFilter.SHOW_TEXT,
  { acceptNode: (node) => NodeFilter.FILTER_ACCEPT },
);
if (
  nodeIterator.whatToShow & NodeFilter.SHOW_ALL ||
  nodeIterator.whatToShow & NodeFilter.SHOW_COMMENT
) {
  // nodeIterator will show comments
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 该属性所属的接口：{{domxref("NodeIterator")}}。