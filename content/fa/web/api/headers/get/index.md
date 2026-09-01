---
title: "Headers: get() method"
---

---
title: "Headers: get() method"
short-title: get()
slug: Web/API/Headers/get
page-type: web-api-instance-method
browser-compat: api.Headers.get
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`get()`** در رابط {{domxref("Headers")}} یک رشتهٔ بایتی از تمام مقادیر یک هدر را که با نام مشخصی در شیء `Headers` قرار دارد، برمی‌گرداند. اگر هدر درخواست‌شده در شیء `Headers` وجود نداشته باشد، مقدار `null` بازگردانده می‌شود.

به دلایل امنیتی، برخی هدرها فقط توسط عامل کاربر (user agent) قابل کنترل هستند. این هدرها شامل {{Glossary("Forbidden_request_header", "forbidden request headers")}} (هدرهای درخواست ممنوع) و {{Glossary("Forbidden_response_header_name", "forbidden response header names")}} (نام‌های هدر پاسخ ممنوع) می‌شوند.

## سینتکس

```js-nolint
get(name)
```

### پارامترها

- `name`
  - : نام هدر HTTP که می‌خواهید مقادیر آن را از شیء `Headers` دریافت کنید. اگر نام داده‌شده با قاعدهٔ تولید (production) [field-name](https://httpwg.org/specs/rfc9110.html#fields.names) در مشخصات HTTP مطابقت نداشته باشد، این متد یک {{jsxref("TypeError")}} پرتاب می‌کند. نام به حروف بزرگ و کوچک حساس نیست.

### مقدار بازگشتی

یک {{jsxref("String")}} که نشان‌دهندهٔ مقادیر هدر بازیابی‌شده است یا اگر هدر مورد نظر تنظیم نشده باشد، `null`.

## مثال‌ها

ساخت یک شیء `Headers` خالی ساده است:

```js
const myHeaders = new Headers(); // Currently empty
myHeaders.get("Not-Set"); // Returns null
```

می‌توانید با استفاده از {{domxref("Headers.append")}} یک هدر به این شیء اضافه کنید و سپس با `get()` آن را بازیابی کنید:

```js
myHeaders.append("Content-Type", "image/jpeg");
myHeaders.get("Content-Type"); // Returns "image/jpeg"
```

اگر هدر چند مقدار داشته باشد، رشتهٔ بایستی شامل تمام مقادیر به ترتیبی است که به شیء `Headers` اضافه شده‌اند:

```js
myHeaders.append("Accept-Encoding", "deflate");
myHeaders.append("Accept-Encoding", "gzip");
myHeaders.get("Accept-Encoding"); // Returns "deflate, gzip"
myHeaders
  .get("Accept-Encoding")
  .split(",")
  .map((v) => v.trimStart()); // Returns [ "deflate", "gzip" ]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)