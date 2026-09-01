---
title: "Headers: set() method"
short-title: set()
slug: Web/API/Headers/set
page-type: web-api-instance-method
browser-compat: api.Headers.set
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`set()`** از رابط {{domxref("Headers")}} یک مقدار جدید برای یک هدر موجود در یک شیء `Headers` تنظیم می‌کند، یا اگر هدر از قبل وجود نداشته باشد، آن را اضافه می‌کند.

تفاوت بین `set()` و {{domxref("Headers.append")}} این است که اگر هدر مشخص شده از قبل وجود داشته باشد و مقادیر متعدد را بپذیرد، `set()` مقدار موجود را با مقدار جدید بازنویسی می‌کند، در حالی که {{domxref("Headers.append")}} مقدار جدید را به انتهای مجموعه مقادیر اضافه می‌کند.

به دلایل امنیتی، برخی از هدرها فقط توسط عامل کاربر (user agent) قابل کنترل هستند. این هدرها شامل {{Glossary("Forbidden_request_header", "هدرهای درخواست ممنوع")}} و {{Glossary("Forbidden_response_header_name", "نام‌های هدر پاسخ ممنوع")}} می‌شوند.

## سینتکس

```js-nolint
set(name, value)
```

### پارامترها

- `name`
  - : نام هدر HTTP که می‌خواهید آن را به یک مقدار جدید تنظیم کنید. اگر نام داده شده نام یک هدر HTTP نباشد، این متد یک {{jsxref("TypeError")}} پرتاب می‌کند.
- `value`
  - : مقدار جدیدی که می‌خواهید تنظیم کنید.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

ایجاد یک شیء خالی `Headers` ساده است:

```js
const myHeaders = new Headers(); // Currently empty
```

می‌توانید با استفاده از {{domxref("Headers.append")}} یک هدر به آن اضافه کنید، سپس با استفاده از `set()` یک مقدار جدید برای این هدر تنظیم کنید:

```js
myHeaders.append("Content-Type", "image/jpeg");
myHeaders.set("Content-Type", "text/html");
```

اگر هدر مشخص شده از قبل وجود نداشته باشد، `set()` آن را ایجاد کرده و مقدار آن را به مقدار مشخص شده تنظیم می‌کند. اگر هدر مشخص شده از قبل وجود داشته باشد و مقادیر متعدد را بپذیرد، `set()` مقدار موجود را با مقدار جدید بازنویسی می‌کند:

```js
myHeaders.set("Accept-Encoding", "deflate");
myHeaders.set("Accept-Encoding", "gzip");
myHeaders.get("Accept-Encoding"); // Returns 'gzip'
```

برای افزودن مقدار جدید به مجموعه مقادیر (بدون بازنویسی) باید از {{domxref("Headers.append")}} استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)