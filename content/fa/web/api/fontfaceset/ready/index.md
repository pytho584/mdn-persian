---
title: "FontFaceSet: ready property"
short-title: ready
slug: Web/API/FontFaceSet/ready
page-type: web-api-instance-property
browser-compat: api.FontFaceSet.ready
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی `ready` از رابط {{domxref("FontFaceSet")}} یک {{jsxref("Promise")}} برمی‌گرداند که با همان {{domxref("FontFaceSet")}} داده شده، برآورده می‌شود.

این پرامیس تنها زمانی برآورده می‌شود که بارگذاری قلم‌ها در سند کامل شده، عملیات چیدمان به پایان رسیده و بارگذاری قلم بیشتری نیاز نباشد.

## مقدار

یک {{jsxref("Promise")}} که با {{domxref("FontFaceSet")}} داده شده برآورده می‌شود.

## مثال‌ها

در مثال زیر، مقدار `ready` پس از برآورده شدن پرامیس در کنسول چاپ می‌شود.

```js
async function isReady() {
  let ready = await document.fonts.ready;
  console.log(ready);
}

isReady();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}