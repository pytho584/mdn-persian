---
title: "EcdsaParams"
---

---
title: EcdsaParams
slug: Web/API/EcdsaParams
page-type: web-api-interface
browser-compat:
  - api.SubtleCrypto.sign
  - api.SubtleCrypto.verify
---

{{ APIRef("Web Crypto API") }}

دیکشنری **`EcdsaParams`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیءای را نشان می‌دهد که هنگام استفاده از الگوریتم [ECDSA](/en-US/docs/Web/API/SubtleCrypto/sign#ecdsa) باید به‌عنوان پارامتر `algorithm` به {{domxref("SubtleCrypto.sign()")}} یا {{domxref("SubtleCrypto.verify()")}} ارسال شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته (string). این مقدار باید روی `ECDSA` تنظیم شود.
- `hash`
  - : یک رشته یا یک شیء شامل یک ویژگی واحد به نام `name` با مقدار رشته‌ای. این شناسه‌ای برای [digest algorithm](/en-US/docs/Web/API/SubtleCrypto/digest) مورد استفاده است. این باید یکی از موارد زیر باشد:
    - `SHA-256`: الگوریتم [SHA-256](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-384`: الگوریتم [SHA-384](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-512`: الگوریتم [SHA-512](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.

    > [!WARNING]
    > `SHA-1` نیز در اینجا پشتیبانی می‌شود، اما الگوریتم [SHA-1](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) آسیب‌پذیر در نظر گرفته می‌شود و دیگر نباید استفاده شود.

## مثال‌ها

برای مثال‌ها به {{domxref("SubtleCrypto.sign()")}} یا {{domxref("SubtleCrypto.verify()")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

مرورگرهایی که از الگوریتم «ECDSA» برای روش‌های {{domxref("SubtleCrypto.sign()")}} و {{domxref("SubtleCrypto.verify()")}} پشتیبانی می‌کنند، از این نوع نیز پشتیبانی خواهند کرد.

{{Compat}}

## همچنین ببینید

- {{domxref("SubtleCrypto.sign()")}} و {{domxref("SubtleCrypto.verify()")}}.