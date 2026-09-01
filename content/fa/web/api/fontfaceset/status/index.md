---
title: "FontFaceSet: status property"
short-title: status
slug: Web/API/FontFaceSet/status
page-type: web-api-instance-property
browser-compat: api.FontFaceSet.status
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`status`** در رابط {{domxref("FontFaceSet")}} وضعیت بارگذاری فونت‌های مجموعه را بازمی‌گرداند.

## مقدار

یکی از موارد زیر:

- `"loading"`
- `"loaded"`

## مثال‌ها

در مثال زیر، `status` شیء `FontFaceSet` در کنسول چاپ می‌شود.

```js
console.log(document.fonts.status);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}