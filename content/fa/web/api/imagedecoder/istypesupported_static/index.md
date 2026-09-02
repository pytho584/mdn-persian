```
---
title: "ImageDecoder: isTypeSupported() static method"
---

---
title: "ImageDecoder: isTypeSupported() static method"
short-title: isTypeSupported()
slug: Web/API/ImageDecoder/isTypeSupported_static
page-type: web-api-static-method
browser-compat: api.ImageDecoder.isTypeSupported_static
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد ایستای **`ImageDecoder.isTypeSupported()`** بررسی می‌کند که آیا یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) مشخص می‌تواند توسط عامل کاربر رمزگشایی شود یا خیر.

## نحو

```js-nolint
ImageDecoder.isTypeSupported(type)
```

### پارامترها

- `type`
  - : رشته‌ای شامل [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) است که باید بررسی شود آیا برای رمزگشایی پشتیبانی می‌شود یا خیر.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار بولی (boolean) حل می‌شود و نشان می‌دهد که آیا تصاویر با فرمت `type` می‌توانند توسط API رمزگشایی شوند یا نه.

## مثال‌ها

مثال زیر بررسی می‌کند که آیا تصاویر GIF و PCX برای رمزگشایی پشتیبانی می‌شوند و نتیجه را در کنسول چاپ می‌کند.

```js
let isGifSupported = await ImageDecoder.isTypeSupported("image/gif");
console.log(`GIF supported: ${isGifSupported}`); // Likely true.

let isPcxSupported = await ImageDecoder.isTypeSupported("image/pcx");
console.log(`PCX supported: ${isPcxSupported}`); // Probably false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```