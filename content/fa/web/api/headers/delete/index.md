---
title: "Headers: delete() method"
short-title: delete()
slug: Web/API/Headers/delete
page-type: web-api-instance-method
browser-compat: api.Headers.delete
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`delete()`** از رابط {{domxref("Headers")}} یک هدر را از شیء `Headers` جاری حذف می‌کند.

به دلایل امنیتی، برخی هدرها فقط توسط عامل کاربر قابل کنترل هستند. این هدرها شامل {{Glossary("Forbidden_request_header", "هدرهای درخواست ممنوع")}} و {{Glossary("Forbidden_response_header_name", "نام‌های هدر پاسخ ممنوع")}} می‌شوند.

## Syntax

```js-nolint
delete(name)
```

### پارامترها

- `name`
  - : نام هدر HTTP که می‌خواهید از شیء `Headers` حذف کنید.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

ایجاد یک شیء خالی `Headers` ساده است:

```js
const myHeaders = new Headers(); // Currently empty
```

می‌توانید با استفاده از {{domxref("Headers.append")}} یک هدر به آن اضافه کنید:

```js
myHeaders.append("Content-Type", "image/jpeg");
myHeaders.get("Content-Type"); // Returns 'image/jpeg'
```

سپس می‌توانید دوباره آن را حذف کنید:

```js
myHeaders.delete("Content-Type");
myHeaders.get("Content-Type"); // Returns null, as it has been deleted
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)