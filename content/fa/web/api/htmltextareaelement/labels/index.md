---
title: "HTMLTextAreaElement: labels property"
short-title: labels
slug: Web/API/HTMLTextAreaElement/labels
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.labels
---

{{APIRef("DOM")}}

**`HTMLTextAreaElement.labels`** 只读属性返回一个 {{domxref("NodeList")}}，其中包含与 {{HTMLElement("textArea")}} 元素相关联的 {{HTMLElement("label")}} 元素。

## 值

一个 {{domxref("NodeList")}}，包含与 `<textArea>` 元素关联的 `<label>` 元素。

## 示例

### HTML

```html
<label id="label1" for="test">Label 1</label>
<textarea id="test">Some text</textarea>
<label id="label2" for="test">Label 2</label>
```

### JavaScript

```js
const textArea = document.getElementById("test");
for (const label of textArea.labels) {
  console.log(label.textContent); // "Label 1" and "Label 2"
}
```

{{EmbedLiveSample("Examples", "100%", 100)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}