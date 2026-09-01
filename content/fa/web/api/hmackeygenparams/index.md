---
title: "HmacKeyGenParams"
slug: Web/API/HmacKeyGenParams
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-HmacKeyGenParams
---

{{ APIRef("Web Crypto API") }}

فرهنگ واژه‌نامه **`HmacKeyGenParams`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیئی را نشان می‌دهد که باید به عنوان پارامتر `algorithm` به {{domxref("SubtleCrypto.generateKey()")}}، هنگام تولید یک کلید برای الگوریتم [HMAC](/en-US/docs/Web/API/SubtleCrypto/sign#hmac)، ارسال شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. این باید روی `HMAC` تنظیم شود.

- `hash`
  - : یک رشته یا یک شیء که دارای یک ویژگی به نام `name` با مقدار رشته‌ای است. این شناسه‌ای برای [digest algorithm](/en-US/docs/Web/API/SubtleCrypto/digest) است که باید استفاده شود. باید یکی از موارد زیر باشد:
    - `SHA-256`: الگوریتم [SHA-256](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-384`: الگوریتم [SHA-384](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-512`: الگوریتم [SHA-512](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.

    > [!WARNING]
    > `SHA-1` نیز در اینجا پشتیبانی می‌شود اما الگوریتم [SHA-1](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) آسیب‌پذیر در نظر گرفته می‌شود و دیگر نباید استفاده شود.

- `length` {{optional_inline}}
  - : یک `Number` — طول کلید بر حسب بیت. اگر این مقدار حذف شود، طول کلید برابر با اندازه بلوک تابع هش انتخاب‌شده خواهد بود. مگر اینکه دلیل خوبی برای استفاده از طول متفاوت داشته باشید، این ویژگی را حذف کرده و از پیش‌فرض استفاده کنید.

## مثال‌ها

مثال‌ها را در {{domxref("SubtleCrypto.generateKey()")}} مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

مرورگرهایی که از الگوریتم "HMAC" برای متد {{domxref("SubtleCrypto.generateKey()")}} پشتیبانی می‌کنند، از این نوع پشتیبانی خواهند کرد.

## همچنین ببینید

- {{domxref("SubtleCrypto.generateKey()")}}.