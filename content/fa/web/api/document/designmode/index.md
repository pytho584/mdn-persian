---
title: "Document: designMode property"
short-title: designMode
slug: Web/API/Document/designMode
page-type: web-api-instance-property
browser-compat: api.Document.designMode
---

{{APIRef("DOM")}}

**`document.designMode`** 控制整个文档是否可编辑。有效值为 `"on"` 和 `"off"`。根据规范，此属性默认应为 `"off"`。Firefox 遵循此标准。早期版本的 Chrome 和 IE 默认值为 `"inherit"`。从 Chrome 43 开始，默认值为 `"off"`，且不再支持 `"inherit"`。在 IE6-10 中，该值是大写的。

## 值

一个字符串，指示 `designMode` 是（或应当）设置为开还是关。有效值为 `on` 和 `off`。

## 示例

使 {{HTMLElement("iframe")}} 的文档可编辑：

```js
iframeNode.contentDocument.designMode = "on";
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("HTMLElement.contentEditable")}}