---
title: "NamedNodeMap: length property"
short-title: length
slug: Web/API/NamedNodeMap/length
page-type: web-api-instance-property
browser-compat: api.NamedNodeMap.length
---

{{APIRef("DOM")}}

خاصیتِ **`length`** فقط‌خواندنی در رابط {{domxref("NamedNodeMap")}}، تعداد اشیاء ذخیره‌شده در نقشه است.

## مقدار

عددی که تعداد اشیاء موجود در نقشه را نشان می‌دهد.

## مثال

```html
<pre class="foo" id="bar" contenteditable></pre>
```

```js
const pre = document.querySelector("pre");
const attrMap = pre.attributes;
pre.textContent = `The 'test' attribute contains ${attrMap.length} attributes.\n`;
```

{{EmbedLiveSample("Example", "100%", 20)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}