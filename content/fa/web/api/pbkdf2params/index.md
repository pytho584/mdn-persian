---
title: "Pbkdf2Params"
slug: Web/API/Pbkdf2Params
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-Pbkdf2Params
---

{{ APIRef("Web Crypto API") }}

دیکشنری **`Pbkdf2Params`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیءای را نشان می‌دهد که باید به عنوان پارامتر `algorithm` به متد {{domxref("SubtleCrypto.deriveKey()")}}، هنگام استفاده از الگوریتم [PBKDF2](/en-US/docs/Web/API/SubtleCrypto/deriveKey#pbkdf2)، ارسال شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. باید روی `PBKDF2` تنظیم شود.
- `hash`
  - : یک رشته یا یک شیء حاوی یک ویژگی واحد به نام `name` با مقدار رشته‌ای. این یک شناسه برای [الگوریتم چکیده‌ساز](/en-US/docs/Web/API/SubtleCrypto/digest) مورد استفاده است. باید یکی از موارد زیر باشد:
    - `SHA-256`: الگوریتم [SHA-256](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-384`: الگوریتم [SHA-384](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.
    - `SHA-512`: الگوریتم [SHA-512](/en-US/docs/Web/API/SubtleCrypto/digest#supported_algorithms) را انتخاب می‌کند.

    > [!WARNING]
    > `SHA-1` در بیشتر کاربردهای رمزنگاری آسیب‌پذیر در نظر گرفته می‌شود، اما هنوز در PBKDF2 ایمن محسوب می‌شود. با این حال، توصیه می‌شود در همه جا از آن دوری کنید، مگر اینکه نیاز به استفاده از `SHA-1` داشته باشید. در عوض از یک الگوریتم چکیده‌ساز دیگر استفاده کنید.

- `salt`
  - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یا یک {{jsxref("DataView")}}. باید یک مقدار تصادفی یا شبه‌تصادفی حداقل ۱۶ بایت باشد. برخلاف مواد کلید ورودی که به [`deriveKey()`](/en-US/docs/Web/API/SubtleCrypto/deriveKey) داده می‌شود، `salt` نیازی به مخفی نگه‌داشتن ندارد.
- `iterations`
  - : یک `Number` که نشان‌دهنده تعداد دفعات اجرای تابع هش در `deriveKey()` است. این تعیین می‌کند که عملیات `deriveKey()` چقدر از نظر محاسباتی پرهزینه (یعنی کند) خواهد بود. در این زمینه، کند بودن خوب است، زیرا حمله‌کننده را برای اجرای حمله دیکشنری علیه کلیدها هزینه‌برتر می‌کند. راهنمای کلی این است که تا حد امکان از تکرارهای بیشتر استفاده کنید، مشروط به حفظ سطح قابل قبولی از عملکرد برای برنامه شما.

## مثال‌ها

مثال‌های مربوط به {{domxref("SubtleCrypto.deriveKey()")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

مرورگرهایی که از الگوریتم "PBKDF2" برای متد {{domxref("SubtleCrypto.deriveKey()")}} پشتیبانی می‌کنند، از این نوع پشتیبانی خواهند کرد.

## همچنین ببینید

- {{domxref("SubtleCrypto.deriveKey()")}}.