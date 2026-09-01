---
title: "Headers: has() method"
short-title: has()
slug: Web/API/Headers/has
page-type: web-api-instance-method
browser-compat: api.Headers.has
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`has()`** از رابط {{domxref("Headers")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا یک شیء `Headers` حاوی هدر مشخصی است یا خیر.

به دلایل امنیتی، برخی هدرها فقط توسط عامل کاربر (user agent) قابل کنترل هستند. این هدرها شامل {{Glossary("Forbidden_request_header", "هدرهای درخواست ممنوع")}} و {{Glossary("Forbidden_response_header_name", "نام‌های هدر پاسخ ممنوع")}} می‌شوند.

## Syntax

```js-nolint
has(name)
```

### Parameters

- `name`
  - : نام هدر HTTP که می‌خواهید وجود آن را بررسی کنید. اگر نام داده‌شده یک نام هدر HTTP معتبر نباشد، این متد یک {{jsxref("TypeError")}} پرتاب می‌کند.

### Return value

یک مقدار بولی.

## Examples

ساخت یک شیء `Headers` خالی ساده است:

```js
const myHeaders = new Headers(); // Currently empty
```

می‌توانید با استفاده از {{domxref("Headers.append")}} یک هدر به آن اضافه کنید و سپس وجود آن را با `has()` بررسی کنید:

```js
myHeaders.append("Content-Type", "image/jpeg");
myHeaders.has("Content-Type"); // Returns true
myHeaders.has("Accept-Encoding"); // Returns false
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
