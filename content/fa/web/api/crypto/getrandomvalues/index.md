---
title: "Crypto: getRandomValues() method"
short-title: getRandomValues()
slug: Web/API/Crypto/getRandomValues
page-type: web-api-instance-method
browser-compat: api.Crypto.getRandomValues
---

{{APIRef("Web Crypto API")}}{{AvailableInWorkers}}

روش **`Crypto.getRandomValues()`** به شما امکان می‌دهد مقادیر تصادفی قوی از نظر رمزنگاری (Cryptographically strong) بدست آورید.
آرایه‌ای که به عنوان پارامتر داده می‌شود با اعداد تصادفی (تصادفی به معنای رمزنگاری آن) پر می‌شود.

برای تضمین عملکرد کافی، پیاده‌سازی‌ها از یک مولد اعداد تصادفی واقعی استفاده نمی‌کنند، بلکه از یک مولد اعداد شبه‌تصادفی (Pseudo-random number generator) استفاده می‌کنند که با یک مقدار دارای آنتروپی کافی _seed_ (seed) شده است.
الگوریتم مولد اعداد شبه‌تصادفی (PRNG) ممکن است در بین {{Glossary("user agent", "عامل‌های کاربر")}} متفاوت باشد، اما برای اهداف رمزنگاری مناسب است.

`getRandomValues()` تنها عضو رابط `Crypto` است که می‌توان از یک زمینه ناامن (insecure context) استفاده کرد.

## Syntax

```js-nolint
getRandomValues(typedArray)
```

### پارامترها

- `typedArray`
  - : یک {{jsxref("TypedArray")}} مبتنی بر اعداد صحیح، که یکی از انواع زیر است: {{jsxref("Int8Array")}}، {{jsxref("Uint8Array")}}،
    {{jsxref("Uint8ClampedArray")}}، {{jsxref("Int16Array")}}، {{jsxref("Uint16Array")}}،
    {{jsxref("Int32Array")}}، {{jsxref("Uint32Array")}}، {{jsxref("BigInt64Array")}}،
    {{jsxref("BigUint64Array")}} (اما **نه** `Float16Array`، `Float32Array` و `Float64Array`).
    تمام عناصر آرایه با اعداد تصادفی بازنویسی خواهند شد.

### مقدار بازگشتی

همان آرایه‌ای که به عنوان `typedArray` ارسال شده است، اما محتویات آن با اعداد تصادفی تازه تولید شده جایگزین شده است.
توجه داشته باشید که `typedArray` به صورت درجا (in-place) تغییر می‌کند و هیچ کپی‌ای ساخته نمی‌شود.

### استثناها

- {{domxref("QuotaExceededError")}}
  - : اگر {{jsxref("TypedArray.byteLength", "byteLength")}} آرایه `typedArray` از ۶۵۵۳۶ بیشتر شود، این خطا پرتاب می‌شود.

## نکات استفاده

برای تولید کلید، از روش {{domxref("SubtleCrypto.generateKey", "generateKey()")}} استفاده کنید که تضمین می‌شود در یک زمینه امن اجرا شود.

هیچ درجه حداقلی از آنتروپی توسط مشخصات Web Cryptography الزامی نشده است.
در عوض، به عامل‌های کاربر توصیه می‌شود که بهترین آنتروپی ممکن را هنگام تولید اعداد تصادفی ارائه دهند،
با استفاده از یک مولد اعداد شبه‌تصادفی کارآمد و خوب تعریف‌شده که در خود عامل کاربر تعبیه شده است،
اما با مقادیری که از یک منبع خارجی اعداد شبه‌تصادفی گرفته شده‌اند، مانند یک تابع اعداد تصادفی خاص پلتفرم،
دستگاه `/dev/urandom` یونیکس، یا دیگر منابع داده‌های تصادفی یا شبه‌تصادفی.

## مثال‌ها

```js
const array = new Uint32Array(10);
self.crypto.getRandomValues(array);

console.log("Your lucky numbers:");
for (const num of array) {
  console.log(num);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API)
- {{jsxref("Math.random")}}، یک منبع غیر رمزنگاری از اعداد تصادفی.