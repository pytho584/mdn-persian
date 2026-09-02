---
title: "MutationEvent: attrChange property"
short-title: attrChange
slug: Web/API/MutationEvent/attrChange
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent.attrChange
---

{{APIRef("UI Events")}}{{Deprecated_Header}}{{non-standard_header}}

خاصیت فقط‌خواندنی **`attrChange`** از رابط {{domxref("MutationEvent")}} عددی را برمی‌گرداند که نشان می‌دهد چه نوع تغییری رویداد `DOMAttrModified` را راه‌اندازی کرده است. سه مقدار ممکن عبارتند از `MODIFICATION` (`1`)، `ADDITION` (`2`) یا `REMOVAL` (`3`). این خاصیت برای رویدادهای دیگر معنایی ندارد و در آن صورت مقدار `0` می‌گیرد.

## مقدار

یک عدد صحیح: `0`، `1` (`MODIFICATION`)، `2` (`ADDITION`) یا `3` (`REMOVAL`).

## مثال‌ها

```js
element.addEventListener("DOMAttrModified", (event) => {
  console.log(event.attrChange);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}