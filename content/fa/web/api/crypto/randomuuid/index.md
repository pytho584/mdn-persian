---
title: "Crypto: randomUUID() method"
short-title: randomUUID()
slug: Web/API/Crypto/randomUUID
page-type: web-api-instance-method
browser-compat: api.Crypto.randomUUID
---

{{APIRef("Web Crypto API")}}{{SecureContext_header}}{{AvailableInWorkers}}

متد **`randomUUID()`** در رابط (interface) {{domxref("Crypto")}} برای تولید یک {{Glossary("UUID")}} نسخه ۴ با استفاده از یک مولد اعداد تصادفی امن از نظر رمزنگاری (cryptographically secure random number generator) به کار می‌رود.

## نحو

```js-nolint
randomUUID()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک رشته (string) شامل یک UUID نسخه ۴ به طول ۳۶ کاراکتر که به‌صورت تصادفی تولید شده است.

## مثال‌ها

```js
/* Assuming that self.crypto.randomUUID() is available */

let uuid = self.crypto.randomUUID();
console.log(uuid); // for example "36b8f84d-df4e-4d49-b662-bcde71a8764f"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API)
- {{ domxref("Crypto.getRandomValues") }}، یک منبع برای مقادیر دلخواه بایت‌های تصادفی امن.
