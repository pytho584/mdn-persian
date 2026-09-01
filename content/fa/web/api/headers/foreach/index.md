---
title: "Headers: forEach() method"
short-title: forEach()
slug: Web/API/Headers/forEach
page-type: web-api-instance-method
browser-compat: api.Headers.forEach
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`Headers.forEach()`** یک تابع بازگشتی (callback) را برای هر جفت کلید/مقدار در شیء [`Headers`](/en-US/docs/Web/API/Headers) اجرا می‌کند.

## نحو

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - تابعی که برای هر ورودی در این نگاشت (map) اجرا می‌شود. این تابع آرگومان‌های زیر را دریافت می‌کند:
    - `value`
      - مقدارِ ورودی هدرِ جاری.
    - `key`
      - نامِ ورودی هدرِ جاری.
    - `object`
      - شیء `Headers` که در حال تکرار است.
- `thisArg` {{Optional_Inline}}
  - مقداری که هنگام اجرای `callback` به‌عنوان `this` استفاده می‌شود.

### مقدار بازگشتی

{{jsxref("undefined")}}.

## توضیحات

متد `Headers.forEach()` تابع بازگشتی داده‌شده را یک‌بار برای هر کلیدی از `Headers` که واقعاً وجود دارد اجرا می‌کند. این متد برای کلیدهایی که حذف شده‌اند فراخوانی نمی‌شود؛ با این حال، برای کلیدهایی که وجود دارند اما مقدارشان undefined است، اجرا می‌شود.

## مثال‌ها

### چاپ محتویات شیء Headers

کد زیر برای هر جفت کلید/مقدار در شیء `myHeaders` یک خط در خروجی ثبت می‌کند.

```js
// Create a new test Headers object
const myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Cookie", "This is a demo cookie");
myHeaders.append("compression", "gzip");

// Display the key/value pairs
myHeaders.forEach((value, key) => {
  console.log(`${key} ==> ${value}`);
});
```

نتیجه به صورت زیر است:

```plain
compression ==> gzip
content-type ==> application/json
cookie ==> This is a demo cookie
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`Map.prototype.forEach()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/forEach)
- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
