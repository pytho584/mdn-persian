---
title: "Headers: append() method"
short-title: append()
slug: Web/API/Headers/append
page-type: web-api-instance-method
browser-compat: api.Headers.append
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`append()`** در رابط {{domxref("Headers")}} یک مقدار جدید را به هدر موجود در یک شیء `Headers` اضافه می‌کند، یا اگر آن هدر از قبل وجود نداشته باشد، آن را اضافه می‌کند.

تفاوت بین {{domxref("Headers.set", "set()")}} و `append()` این است که اگر هدر مشخص‌شده از قبل وجود داشته باشد و چند مقدار را بپذیرد، `set()` مقدار موجود را با مقدار جدید بازنویسی می‌کند، در حالی که `append()` مقدار جدید را به انتهای مجموعه مقادیر اضافه می‌کند.

به دلایل امنیتی، برخی هدرها فقط توسط عامل کاربر قابل کنترل هستند. این هدرها شامل {{Glossary("Forbidden_request_header", "forbidden request headers")}} و {{Glossary("Forbidden_response_header_name", "forbidden response header names")}} می‌شوند.

## سینتکس

```js-nolint
append(name, value)
```

### پارامترها

- `name`
  - : نام هدر HTTP که می‌خواهید به شیء `Headers` اضافه کنید.
- `value`
  - : مقدار هدر HTTP که می‌خواهید اضافه کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

ساخت یک شیء `Headers` خالی ساده است:

```js
const myHeaders = new Headers(); // Currently empty
```

می‌توانید با استفاده از `append()` یک هدر به این شیء اضافه کنید:

```js
myHeaders.append("Content-Type", "image/jpeg");
myHeaders.get("Content-Type"); // Returns 'image/jpeg'
```

اگر هدر مشخص‌شده از قبل وجود داشته باشد، `append()` مقدار آن را به مقدار مشخص‌شده تغییر می‌دهد. اگر هدر مشخص‌شده از قبل وجود داشته باشد و چند مقدار را بپذیرد، `append()` مقدار جدید را به انتهای مجموعه مقادیر اضافه می‌کند:

```js
myHeaders.append("Accept-Encoding", "deflate");
myHeaders.append("Accept-Encoding", "gzip");
myHeaders.get("Accept-Encoding"); // Returns 'deflate, gzip'
```

برای بازنویسی مقدار قدیمی با مقدار جدید، از {{domxref("Headers.set")}} استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)