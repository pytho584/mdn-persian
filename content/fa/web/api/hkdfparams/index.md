---
title: HkdfParams
slug: Web/API/HkdfParams
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-HkdfParams
---

{{ APIRef("Web Crypto API") }}

دیکشنری `HkdfParams` از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) نشان‌دهندهٔ شیئی است که باید به عنوان پارامتر `algorithm` در متد {{domxref("SubtleCrypto.deriveKey()")}} هنگام استفاده از الگوریتم [HKDF](/en-US/docs/Web/API/SubtleCrypto/deriveKey#hkdf) ارسال شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. این باید روی `HKDF` تنظیم شود.
- `hash`
  - : یک رشته یا یک شیء که دارای یک ویژگی به نام `name` با مقدار رشته‌ای است. این یک شناسه برای [الگوریتم چکیده](/en-US/docs/Web/API/SubtleCrypto/digest) مورد استفاده است. باید یکی از موارد زیر باشد:
    - `SHA-256`: الگوریتم [SHA-256](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-384`: الگوریتم [SHA-384](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-512`: الگوریتم [SHA-512](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.

    > [!WARNING]
    > `SHA-1` نیز در اینجا پشتیبانی می‌شود، اما الگوریتم [SHA-1](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) آسیب‌پذیر در نظر گرفته می‌شود و دیگر نباید استفاده شود.

- `salt`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}}. [مشخصات HKDF](https://datatracker.ietf.org/doc/html/rfc5869) بیان می‌کند که افزودن salt «به طور قابل توجهی به قدرت HKDF می‌افزاید». در حالت ایده‌آل، salt یک مقدار تصادفی یا شبه‌تصادفی با طول برابر با خروجی تابع چکیده است. برخلاف ماده کلید ورودی که به `deriveKey()` داده می‌شود، salt نیازی به مخفی ماندن ندارد.
- `info`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} نشان‌دهندهٔ اطلاعات زمینه‌ای خاص برنامه. این برای اتصال کلید مشتق‌شده به یک برنامه یا زمینه استفاده می‌شود و به شما امکان می‌دهد کلیدهای متفاوتی برای زمینه‌های مختلف با استفاده از همان ماده کلید ورودی استخراج کنید. مهم است که این باید مستقل از خود ماده کلید ورودی باشد. این ویژگی الزامی است اما ممکن است یک بافر خالی باشد.

## مثال‌ها

مثال‌ها را در صفحهٔ {{domxref("SubtleCrypto.deriveKey()")}} ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

مرورگرهایی که از الگوریتم «HKDF» برای متد {{domxref("SubtleCrypto.deriveKey()")}} پشتیبانی می‌کنند، از این نوع پشتیبانی خواهند کرد.

## همچنین ببینید

- {{domxref("SubtleCrypto.deriveKey()")}}