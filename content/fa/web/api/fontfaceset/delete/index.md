---
title: "FontFaceSet: delete() method"
short-title: delete()
slug: Web/API/FontFaceSet/delete
page-type: web-api-instance-method
browser-compat: api.FontFaceSet.delete
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

متد **`delete()`** در رابط {{domxref("FontFaceSet")}} یک فونت را از مجموعه حذف می‌کند.

فونت‌هایی که با استفاده از قاعده CSS {{cssxref("@font-face")}} به مجموعه اضافه شده‌اند، همچنان به CSS مربوطه متصل می‌مانند و قابل حذف نیستند.

## Syntax

```js-nolint
delete(font)
```

### پارامترها

- `font`
  - : یک {{domxref("FontFace")}} که باید از مجموعه حذف شود.

### مقدار بازگشتی

یک مقدار بولی که در صورت موفقیت‌آمیز بودن حذف، `true` و در غیر این صورت `false` است.

## مثال‌ها

در مثال زیر، یک شیء جدید {{domxref("FontFace")}} ساخته شده و سپس از {{domxref("FontFaceSet")}} حذف می‌شود.

```js
const font = new FontFace("MyFont", 'url("myFont.woff2")');
document.fonts.delete(font);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}