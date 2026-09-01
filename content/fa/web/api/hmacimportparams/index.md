---
title: HmacImportParams
slug: Web/API/HmacImportParams
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-HmacImportParams
---

{{ APIRef("Web Crypto API") }}

دیکشنری **`HmacImportParams`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیئی را نشان می‌دهد که باید هنگام ایمپورت، آن‌راپ یا مشتق‌گیری کلید برای الگوریتم [HMAC](/en-US/docs/Web/API/SubtleCrypto/sign#hmac) ارسال شود؛ به این صورت:

- پارامتر `algorithm` در {{domxref("SubtleCrypto.importKey()")}}
- پارامتر `unwrappedKeyAlgorithm` در {{domxref("SubtleCrypto.unwrapKey()")}}
- پارامتر `derivedKeyType` در {{domxref("SubtleCrypto.deriveKey()")}}

## ویژگی‌های نمونه

- `name`
  - : یک رشته. این مقدار باید روی `HMAC` تنظیم شود.
- `hash`
  - : یک رشته یا یک شیء حاوی یک ویژگی واحد به نام `name` با مقدار رشته‌ای. این مقدار شناسه‌ای برای [الگوریتم چکیده (digest)](/en-US/docs/Web/API/SubtleCrypto/digest) مورد استفاده است و باید یکی از موارد زیر باشد:
    - `SHA-256`: الگوریتم [SHA-256](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-384`: الگوریتم [SHA-384](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-512`: الگوریتم [SHA-512](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.

    > [!WARNING]
    > `SHA-1` نیز در اینجا پشتیبانی می‌شود، اما الگوریتم [SHA-1](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) آسیب‌پذیر شناخته می‌شود و دیگر نباید استفاده شود.

- `length` {{optional_inline}}
  - : یک `Number` که طول کلید را بر حسب بیت نشان می‌دهد. اگر این ویژگی حذف شود، طول کلید با طول چکیده‌ای که توسط تابع چکیده‌ساز انتخاب‌شده تولید می‌شود برابر خواهد بود. مگر اینکه دلیل موجهی برای استفاده از طول متفاوت داشته باشید، این ویژگی را حذف کنید و از مقدار پیش‌فرض استفاده کنید.

## مثال‌ها

برای مشاهده مثال‌ها، به {{domxref("SubtleCrypto.importKey()")}}، {{domxref("SubtleCrypto.unwrapKey()")}} یا {{domxref("SubtleCrypto.deriveKey()")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

مرورگرهایی که الگوریتم "HMAC" را برای متدهای {{domxref("SubtleCrypto.importKey()")}}، {{domxref("SubtleCrypto.unwrapKey()")}} یا {{domxref("SubtleCrypto.deriveKey()")}} پشتیبانی می‌کنند، این نوع را نیز پشتیبانی خواهند کرد.

## همچنین ببینید

- {{domxref("SubtleCrypto.importKey()")}}.
- {{domxref("SubtleCrypto.unwrapKey()")}}.
- {{domxref("SubtleCrypto.deriveKey()")}}.