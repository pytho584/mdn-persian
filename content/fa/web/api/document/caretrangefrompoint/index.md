---
title: "Document: caretRangeFromPoint() method"
short-title: caretRangeFromPoint()
slug: Web/API/Document/caretRangeFromPoint
page-type: web-api-instance-method
status:
  - non-standard
browser-compat: api.Document.caretRangeFromPoint
---

{{APIRef("DOM")}}{{Non-standard_header}}

**`caretRangeFromPoint()`** 方法属于 {{domxref("Document")}} 接口，会针对指定坐标处的文档片段返回一个 {{domxref("Range")}} 对象。

此方法早于 Shadow DOM 的概念而存在，因此在包含 {{domxref("ShadowRoot")}} 对象的文档中，它会返回不可预测且依赖于具体实现的结果。

在支持的浏览器中，请改用 {{domxref("Document/caretPositionFromPoint", "caretPositionFromPoint()")}}，因为这是一个标准方法，只要相关的 shadow root 通过其 `options` 参数传入，它就能返回这些 {{domxref("ShadowRoot")}} 实例内部的插入符位置。

## 语法

```js-nolint
caretRangeFromPoint(x, y)
```

### 参数

- `x`
  - : 当前视口内的水平位置。
- `y`
  - : 当前视口内的垂直位置。

### 返回值

以下之一：

- 一个 {{domxref("Range")}}。
- 如果 _x_ 或 _y_ 为负值、超出视口，或不存在文本输入节点，则为 `null`。

## 示例

请访问 {{domxref("Document/caretPositionFromPoint#Examples", "Document.caretPositionFromPoint()")}} 页面查看此方法的实时示例。

## 规范

不属于任何规范。

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Document.caretPositionFromPoint()")}}