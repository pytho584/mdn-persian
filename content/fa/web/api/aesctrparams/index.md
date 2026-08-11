---
title: "AesCtrParams"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AesCtrParams"
translated_by: "n8n + AI"
---

## AesCtrParams

دیکشنری **`AesCtrParams`** در [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) نمایانگر شی‌ای است که هنگام استفاده از الگوریتم [AES-CTR](/en-US/docs/Web/API/SubtleCrypto/encrypt#aes-ctr) باید به‌عنوان پارامتر `algorithm` به متدهای [`SubtleCrypto.encrypt()`](/en-US/docs/Web/API/SubtleCrypto/encrypt)، [`SubtleCrypto.decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt)، [`SubtleCrypto.wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey) یا [`SubtleCrypto.unwrapKey()`](/en-US/docs/Web/API/SubtleCrypto/unwrapKey) ارسال شود.

AES یک رمزنگاری بلاکی (block cipher) است؛ یعنی پیام را به بلاک‌هایی تقسیم می‌کند و هر بلاک را جداگانه رمز می‌کند. در مد CTR، هر بار که بلاکی از پیام رمز می‌شود، یک بلاک اضافی از داده هم در آن ترکیب می‌شود. به این بلاک اضافی «counter block» می‌گویند.

یک مقدار مشخص از counter block نباید بیش از یک بار با یک کلید یکسان استفاده شود:

- اگر پیامی به طول _n_ بلاک داشته باشیم، برای هر بلاک باید از یک counter block متفاوت استفاده کرد.
- اگر از یک کلید برای رمزنگاری بیش از یک پیام استفاده شود، باید برای تمام بلاک‌های تمام پیام‌ها از counter blockهای متفاوت بهره برد.

معمولاً این کار با تقسیم مقدار اولیهٔ counter block به دو بخش انجام می‌شود که به هم الصاق می‌شوند:

- یک [nonce](/en-US/docs/Glossary/Nonce) (یعنی عددی که فقط یک‌بار می‌تواند استفاده شود). بخش nonce از بلاک برای تمام بلاک‌های یک پیام ثابت می‌ماند. هر بار که پیام جدیدی رمز می‌شود، یک nonce جدید انتخاب می‌شود. nonceها نیازی به مخفی بودن ندارند، اما نباید با همان کلید دوباره استفاده شوند.
- یک شمارنده (counter). این بخش از بلاک با هر بار رمز شدن یک بلاک، افزایش می‌یابد.

در اصل: nonce تضمین می‌کند که counter blockها بین پیام‌های مختلف تکراری نباشند و شمارنده هم تضمین می‌کند که درون یک پیام single، counter blockها تکراری نشوند.

> [!NOTE]
> برای اطلاعات بیشتر به [Appendix B of the NIST SP800-38A standard](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38a.pdf#%5B%7B%22num%22%3A70%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22Fit%22%7D%5D) مراجعه کنید.

## ویژگی‌های نمونه (Instance properties)

- `name`
  - : یک رشته. باید مقدار آن `AES-CTR` باشد.
- `counter`
  - : یک [`ArrayBuffer`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)، [`TypedArray`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray) یا [`DataView`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/DataView) — مقدار اولیهٔ counter block. باید دقیقاً ۱۶ بایت باشد (اندازهٔ بلاک AES). `length` بیت سمت راست این بلاک برای شمارنده استفاده می‌شود و بقیه به nonce اختصاص می‌یابد. برای مثال، اگر `length` برابر با ۶۴ تنظیم شود، نیمهٔ اول `counter` نقش nonce و نیمهٔ دوم نقش شمارنده را دارد.
- `length`
  - : یک عدد (`Number`) — تعداد بیت‌هایی از counter block که برای شمارندهٔ واقعی به کار می‌روند. شمارنده باید آن‌قدر بزرگ باشد که سرریز نکند: اگر پیام `n` بلاک داشته باشد و شمارنده `m` بیت طول داشته باشد، آن‌گاه باید `n <= 2^m` برقرار باشد. استاندارد [NIST SP800-38A](https://csrc.nist.gov/pubs/sp/800/38/a/final) که مد CTR را تعریف می‌کند، پیشنهاد می‌دهد شمارنده نیمی از counter block را اشغال کند (به [Appendix B.2](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38a.pdf#%5B%7B%22num%22%3A73%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22Fit%22%7D%5D) مراجعه کنید)، بنابراین برای AES این مقدار ۶۴ خواهد بود.

## مثال‌ها

مثال‌های مربوط به [`SubtleCrypto.encrypt()`](/en-US/docs/Web/API/SubtleCrypto/encrypt) و [`SubtleCrypto.decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt) را ببینید.

## مشخصات (Specifications)

## سازگاری مرورگرها

مرورگرهایی که از الگوریتم "AES-CTR" در متدهای [`SubtleCrypto.encrypt()`](/en-US/docs/Web/API/SubtleCrypto/encrypt)، [`SubtleCrypto.decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt)، [`SubtleCrypto.wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey) یا [`SubtleCrypto.unwrapKey()`](/en-US/docs/Web/API/SubtleCrypto/unwrapKey) پشتیبانی می‌کنند، از این نوع نیز پشتیبانی خواهند کرد.

## جستارهای وابسته

- حالت CTR در بخش 6.5 از [استاندارد NIST SP800-38A](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38a.pdf#%5B%7B%22num%22%3A70%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22Fit%22%7D%5D) تعریف شده است.
- `SubtleCrypto.encrypt()`
- `SubtleCrypto.decrypt()`
- `SubtleCrypto.wrapKey()`
- `SubtleCrypto.unwrapKey()`