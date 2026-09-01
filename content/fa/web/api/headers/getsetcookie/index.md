---
title: "Headers: getSetCookie() method"
short-title: getSetCookie()
slug: Web/API/Headers/getSetCookie
page-type: web-api-instance-method
browser-compat: api.Headers.getSetCookie
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`getSetCookie()`** از رابط {{domxref("Headers")}} آرایه‌ای شامل مقادیر تمام هدرهای {{httpheader("Set-Cookie")}} مرتبط با یک پاسخ را برمی‌گرداند. این امکان را به اشیاء {{domxref("Headers")}} می‌دهد که چندین هدر `Set-Cookie` را مدیریت کنند، کاری که قبل از پیاده‌سازی این متد ممکن نبود.

این متد برای استفاده در محیط‌های سرور (مانند Node.js) در نظر گرفته شده است. مرورگرها دسترسی کد جاوااسکریپت سمت کاربر (frontend) به هدر {{httpheader("Set-Cookie")}} را مسدود می‌کنند، همانطور که توسط مشخصات Fetch الزامی شده است، که `Set-Cookie` را به عنوان [نام هدر پاسخ ممنوع](https://fetch.spec.whatwg.org/#forbidden-response-header-name) تعریف می‌کند که باید از هر پاسخی که در معرض کد سمت کاربر قرار می‌گیرد [فیلتر شود](https://fetch.spec.whatwg.org/#ref-for-forbidden-response-header-name%E2%91%A0).

## نحو (Syntax)

```js-nolint
getSetCookie()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

آرایه‌ای از رشته‌ها که مقادیر تمام هدرهای `Set-Cookie` مختلف مرتبط با یک پاسخ را نشان می‌دهد.

اگر هیچ هدر `Set-Cookie`ای تنظیم نشده باشد، متد یک آرایه خالی (`[ ]`) برمی‌گرداند.

## مثال‌ها

همانطور که در بالا اشاره شد، اجرای کدی مانند زیر در سمت کلاینت هیچ نتیجه‌ای برنمی‌گرداند — `Set-Cookie` از {{domxref("Headers")}} دریافت‌شده از طریق شبکه فیلتر می‌شود.

```js
fetch("https://example.com").then((response) => {
  console.log(response.headers.getSetCookie());
  // No header values returned
});
```

با این حال، می‌توان از کد زیر برای پرس‌وجوی چندین مقدار `Set-Cookie` استفاده کرد. این کار در سمت سرور بسیار مفیدتر است، اما در سمت کلاینت نیز کار می‌کند.

```js
const headers = new Headers({
  "Set-Cookie": "name1=value1",
});

headers.append("Set-Cookie", "name2=value2");

headers.getSetCookie();
// Returns ["name1=value1", "name2=value2"]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [HTTP](/en-US/docs/Web/HTTP)
- {{httpheader("Set-Cookie")}}