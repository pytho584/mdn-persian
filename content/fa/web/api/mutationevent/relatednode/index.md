---
title: "MutationEvent: relatedNode property"
short-title: relatedNode
slug: Web/API/MutationEvent/relatedNode
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent.relatedNode
---

{{APIRef("UI Events")}}{{Deprecated_Header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`relatedNode`** از رابط {{domxref("MutationEvent")}} رشته‌ای را برمی‌گرداند که گره مرتبط با رویداد را نشان می‌دهد، مانند گره تغییر یافته در زیردرخت برای رویداد `DOMSubtreeModified`.

## مقدار

یک رشته.

## مثال‌ها

```js
element.addEventListener("DOMSubtreeModified", (event) => {
  console.log(event.relatedNode);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}