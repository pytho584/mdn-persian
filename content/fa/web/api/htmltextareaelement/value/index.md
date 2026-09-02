---
title: "HTMLTextAreaElement: value property"
short-title: value
slug: Web/API/HTMLTextAreaElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.value
---

{{ APIRef("HTML DOM") }}

ویژگی **`value`** از رابط {{DOMxRef("HTMLTextAreaElement")}} نمایانگر مقدار عنصر {{htmlelement("textarea")}} به صورت یک رشته است. اگر ویجت حاوی هیچ محتوایی نباشد، این مقدار یک رشته خالی خواهد بود. این ویژگی مقدار خام موجود در کنترل را بازمی‌گرداند یا تنظیم می‌کند.

## Value

یک رشته شامل محتویات عنصر {{htmlelement("textarea")}}.

## Examples

```js
const textareaElement = document.getElementById("comment");
const oldText = textArea.value;
textArea.value = oldText.toUpperCase();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.textLength")}}
- {{DOMXref("HTMLTextAreaElement.labels")}}
- {{DOMXref("HTMLTextAreaElement.selectionStart")}}
- {{DOMXref("HTMLTextAreaElement.selectionEnd")}}