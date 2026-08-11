---
title: "AesGcmParams"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AesGcmParams"
translated_by: "n8n + AI"
---

دیکشنری **`AesGcmParams`** در [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیءای را تعریف می‌کند که باید به‌عنوان پارامتر `algorithm` به متدهای [`SubtleCrypto.encrypt()`](/en-US/docs/Web/API/SubtleCrypto/encrypt)، [`SubtleCrypto.decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt)، [`SubtleCrypto.wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey) یا [`SubtleCrypto.unwrapKey()`](/en-US/docs/Web/API/SubtleCrypto/unwrapKey) ارسال شود، زمانی که از الگوریتم [AES-GCM](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-gcm) استفاده می‌کنید.

برای جزئیات نحوهٔ تأمین مقادیر مناسب برای این پارامتر، مشخصهٔ AES-GCM را مطالعه کنید: [NIST SP800-38D](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf)، به‌ویژه بخش ۵.۲.۱.۱ دربارهٔ داده‌های ورودی.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. باید روی `AES-GCM` تنظیم شود.
- `iv`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} که بردار اولیه (initialization vector) را در خود دارد. این مقدار برای هر عملیات رمزنگاری که با کلید مشخصی انجام می‌شود باید یکتا باشد. به بیان دیگر: هرگز با همان کلید از یک IV تکراری استفاده نکنید. مشخصهٔ AES-GCM توصیه می‌کند که IV طولی برابر ۹۶ بیت داشته باشد و معمولاً شامل بیت‌هایی از یک مولد اعداد تصادفی است. [بخش ۸.۲ مشخصه](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf#%5B%7B%22num%22%3A65%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C792%2Cnull%5D) روش‌هایی برای ساخت IV تشریح می‌کند. توجه کنید که IV نیازی به محرمانه بودن ندارد، فقط باید یکتا باشد؛ بنابراین می‌توانید آن را مثلاً به‌صورت آشکار همراه پیام رمزنگاری‌شده منتقل کنید.
- `additionalData` {{optional_inline}}
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} که حاوی داده‌های اضافی است. این داده‌ها رمزنگاری نخواهند شد اما همراه داده‌های رمزنگاری‌شده احراز هویت می‌گردند. اگر اینجا `additionalData` ارائه شود، همان داده‌ها باید در فراخوانی متناظر [`decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt) نیز داده شود: اگر داده‌ای که به فراخوانی `decrypt()` ارسال می‌شود با دادهٔ اصلی مطابقت نداشته باشد، عملیات رمزگشایی یک استثنا پرتاب خواهد کرد. به این ترتیب می‌توانید داده‌های وابسته را بدون نیاز به رمزنگاری احراز هویت کنید.

    طول بیتی `additionalData` باید کمتر از `2^64 - 1` باشد.

    ویژگی `additionalData` اختیاری است و می‌توان آن را بدون به‌خطر افتادن امنیت عملیات رمزنگاری حذف کرد.

- `tagLength` {{optional_inline}}
  - : یک `Number` که اندازه (بر حسب بیت) برچسب تایید (authentication tag) تولیدشده در عملیات رمزنگاری و استفاده‌شده برای احراز هویت در عملیات رمزگشایی متناظر را مشخص می‌کند.

    بر اساس [مشخصهٔ Web Crypto API](https://w3c.github.io/webcrypto/#aes-gcm-operations-encrypt) این مقدار باید یکی از موارد زیر باشد: ۳۲, ۶۴, ۹۶, ۱۰۴, ۱۱۲, ۱۲۰, یا ۱۲۸. از سوی دیگر، مشخصهٔ AES-GCM توصیه می‌کند که این مقدار ۹۶, ۱۰۴, ۱۱۲, ۱۲۰, یا ۱۲۸ باشد، هرچند ۳۲ یا ۶۴ بیت هم در برخی کاربردها ممکن است قابل قبول باشد. برای راهنمایی بیشتر، [ضمیمهٔ C](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf#%5B%7B%22num%22%3A92%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C792%2Cnull%5D) انتشارات NIST دربارهٔ «توصیه برای حالت‌های عملیات رمزنگاری بلوکی» را ببینید.

    `tagLength` اختیاری است و در صورت عدم تعیین، مقدار پیش‌فرض آن ۱۲۸ خواهد بود.

## مثال‌ها

نمونه‌های استفاده را در مستندات [`SubtleCrypto.encrypt()`](/en-US/docs/Web/API/SubtleCrypto/encrypt) و [`SubtleCrypto.decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt) ببینید.

- `SubtleCrypto.encrypt()`.
- `SubtleCrypto.decrypt()`.
- `SubtleCrypto.wrapKey()`.
- `SubtleCrypto.unwrapKey()`.