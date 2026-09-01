---
title: "HTMLMediaElement: muted property"
short-title: muted
slug: Web/API/HTMLMediaElement/muted
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.muted
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.muted`** نشان می‌دهد که آیا عنصر رسانه‌ای بی‌صدا است یا خیر.

## مقدار

یک مقدار بولین. `true` به معنای بی‌صدا بودن و `false` به معنای بی‌صدا نبودن است.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.muted); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف ویژگی `HTMLMediaElement.muted` استفاده شده است
- {{domxref("HTMLMediaElement.defaultMuted")}}
- {{domxref("HTMLMediaElement.volume")}}