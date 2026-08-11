---
title: "AesDerivedKeyParams"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AesDerivedKeyParams"
translated_by: "n8n + AI"
---

# AesDerivedKeyParams

فرهنگ (dictionary) **`AesDerivedKeyParams`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیء‌ای را نشان می‌دهد که باید به‌عنوان پارامتر `derivedKeyType` به متد [`SubtleCrypto.deriveKey()`](/en-US/docs/Web/API/SubtleCrypto/deriveKey) ارسال شود، وقتی که یک کلید AES استخراج می‌کنید: یعنی وقتی الگوریتم به‌عنوان یکی از [AES-CBC](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-cbc)، [AES-CTR](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-ctr)، [AES-GCM](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-gcm) یا [AES-KW](/en-US/docs/Web/API/SubtleCrypto/wrapKey#aes-kw) مشخص شده باشد.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. باید روی `AES-CBC`، `AES-CTR`، `AES-GCM`، یا `AES-KW` تنظیم شود، بسته به الگوریتمی که می‌خواهید استفاده کنید.
- `length`
  - : یک `Number` — طول کلید به بیت که باید تولید شود. باید یکی از مقادیر: 128، 192، یا 256 باشد.

## مثال‌ها

نمونه‌ها را در [`SubtleCrypto.deriveKey()`](/en-US/docs/Web/API/SubtleCrypto/deriveKey) ببینید.

## سازگاری مرورگرها

مرورگرهایی که هر یک از الگوریتم‌های مبتنی بر AES را در متد [`SubtleCrypto.deriveKey()`](/en-US/docs/Web/API/SubtleCrypto/deriveKey) پشتیبانی می‌کنند، این نوع را نیز پشتیبانی خواهند کرد.

## همچنین ببینید

- [`SubtleCrypto.generateKey()`](/en-US/docs/Web/API/SubtleCrypto/generateKey)