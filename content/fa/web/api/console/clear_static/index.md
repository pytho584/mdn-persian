---
title: "console: clear() static method"
short-title: clear()
slug: Web/API/console/clear_static
page-type: web-api-static-method
browser-compat: api.console.clear_static
---

{{APIRef("Console API")}}

متد استاتیک **`console.clear()`** در صورت امکان، کنسول را پاک می‌کند.

یک کنسول گرافیکی، مانند کنسول مرورگرهای وب، تمام پیام‌های قبلی را حذف می‌کند؛ کنسولی که روی ترمینال نمایش داده می‌شود، مانند کنسول Node.js، تلاش می‌کند با استفاده از یک کد فرار (escape code) یا API سیستمی آن را پاک کند؛ در غیر این صورت، این متد هیچ اثری ندارد (و هیچ خطایی هم ایجاد نمی‌کند).

## نحو

```js-nolint
console.clear()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.clear()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#clear)
- [مستندات Node.js برای `console.clear()`](https://nodejs.org/docs/latest/api/console.html#consoleclear)
- [مستندات Google Chrome برای `console.clear()`](https://developer.chrome.com/docs/devtools/console/api/#clear)