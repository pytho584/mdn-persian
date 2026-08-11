---
title: "AesKeyGenParams"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AesKeyGenParams"
translated_by: "n8n + AI"
---

# AesKeyGenParams

دیکشنری **`AesKeyGenParams`** در [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیءای را مشخص می‌کند که هنگام تولید یک کلید AES باید به‌عنوان پارامتر `algorithm` به `SubtleCrypto.generateKey()` ارسال شود؛ یعنی زمانی که الگوریتم انتخابی یکی از [AES-CBC](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-cbc)، [AES-CTR](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-ctr)، [AES-GCM](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-gcm) یا [AES-KW](/en-US/docs/Web/API/SubtleCrypto/wrapKey#aes-kw) باشد.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. بسته به الگوریتمی که می‌خواهید استفاده کنید، باید روی یکی از مقادیر `AES-CBC`، `AES-CTR`، `AES-GCM` یا `AES-KW` تنظیم شود.
- `length`
  - : یک `Number` — طول کلید تولیدی بر حسب بیت. باید یکی از ۱۲۸، ۱۹۲ یا ۲۵۶ باشد.

## مثال‌ها

برای دیدن مثال‌ها، به مستندات `SubtleCrypto.generateKey()` مراجعه کنید.

## سازگاری مرورگرها

مرورگرهایی که از هر یک از الگوریتم‌های مبتنی بر AES برای متد `SubtleCrypto.generateKey()` پشتیبانی می‌کنند، از این نوع نیز پشتیبانی خواهند کرد.

## همچنین ببینید

- `SubtleCrypto.generateKey()`