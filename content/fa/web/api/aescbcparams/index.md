---
title: "AesCbcParams"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AesCbcParams"
translated_by: "n8n + AI"
---

# AesCbcParams

دیکشنری **`AesCbcParams`** در [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) نشان‌دهندهٔ شیءای است که هنگام استفاده از الگوریتم [AES-CBC](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-cbc) باید به‌عنوان پارامتر `algorithm` به متدهای {{domxref("SubtleCrypto.encrypt()")}}، {{domxref("SubtleCrypto.decrypt()")}}، {{domxref("SubtleCrypto.wrapKey()")}} و {{domxref("SubtleCrypto.unwrapKey()")}} ارسال شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. باید مقدار `AES-CBC` را داشته باشد.
- `iv`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}}. بردار اولیه (initialization vector) را مشخص می‌کند. باید ۱۶ بایت، غیرقابل پیش‌بینی و ترجیحاً تصادفی رمزنگاری‌شده باشد. با این‌حال محرمانه بودن آن الزامی نیست (برای نمونه، می‌تواند به‌همراه متن رمزشده و بدون رمزنگاری منتقل شود).

## مثال‌ها

برای نمونه‌ها، به مستندات {{domxref("SubtleCrypto.encrypt()")}} و {{domxref("SubtleCrypto.decrypt()")}} مراجعه کنید.

## مشخصات

برای جزئیات دقیق به [مشخصات Web Crypto API](https://w3c.github.io/webcrypto/#dfn-AesCbcParams) مراجعه کنید.

## سازگاری مرورگر

مرورگرهایی که از الگوریتم AES-CBC برای متدهای {{domxref("SubtleCrypto.encrypt()")}}، {{domxref("SubtleCrypto.decrypt()")}}، {{domxref("SubtleCrypto.wrapKey()")}} یا {{domxref("SubtleCrypto.unwrapKey()")}} پشتیبانی می‌کنند، از این نوع نیز پشتیبانی خواهند کرد.

## همچنین ببینید

- حالت CBC در بخش ۶.۲ استاندارد [NIST SP800-38A](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38a.pdf#%5B%7B%22num%22%3A70%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22Fit%22%7D%5D) تعریف شده است.
- {{domxref("SubtleCrypto.encrypt()")}}
- {{domxref("SubtleCrypto.decrypt()")}}
- {{domxref("SubtleCrypto.wrapKey()")}}
- {{domxref("SubtleCrypto.unwrapKey()")}}