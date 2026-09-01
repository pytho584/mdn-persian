---
title: "EcdhKeyDeriveParams"
---

---
title: EcdhKeyDeriveParams
slug: Web/API/EcdhKeyDeriveParams
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-EcdhKeyDeriveParams
---

{{ APIRef("Web Crypto API") }}

دیکشنری **`EcdhKeyDeriveParams`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) شیئی را نشان می‌دهد که باید به عنوان پارامتر `algorithm` به متدهای {{domxref("SubtleCrypto.deriveKey()")}} و {{domxref("SubtleCrypto.deriveBits()")}}، هنگام استفاده از الگوریتم‌های [ECDH](/en-US/docs/Web/API/SubtleCrypto/deriveKey#ecdh) یا [X25519](/en-US/docs/Web/API/SubtleCrypto/deriveKey#x25519) ارسال شود.

ECDH به دو نفر که هر کدام یک جفت کلید شامل یک کلید عمومی و یک کلید خصوصی دارند، امکان می‌دهد تا یک راز مشترک استخراج کنند. آنها کلیدهای عمومی را مبادله کرده و با ترکیب کلید خصوصی خود و کلید عمومی طرف مقابل، یک کلید مخفی را استخراج می‌کنند که تنها آنها — و هیچ‌کس دیگر — آن را به اشتراک می‌گذارند.

بنابراین پارامترهای `deriveKey()` در ECDH شامل کلید عمومی طرف مقابل است که با کلید خصوصی این طرف ترکیب می‌شود تا راز مشترک استخراج شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. این باید بسته به الگوریتم مورد استفاده، روی `ECDH` یا `X25519` تنظیم شود.
- `public`
  - : یک شیء {{domxref("CryptoKey")}} که کلید عمومی طرف مقابل را نشان می‌دهد.

## مثال‌ها

مثال‌ها را در صفحات {{domxref("SubtleCrypto.deriveKey()")}} و {{domxref("SubtleCrypto.deriveBits()")}} مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

مرورگرهایی که از الگوریتم "ECDH" یا "X25519" برای متد {{domxref("SubtleCrypto.deriveKey()")}} پشتیبانی می‌کنند، این نوع را نیز پشتیبانی خواهند کرد.

## همچنین ببینید

- {{domxref("SubtleCrypto.deriveKey()")}}
- {{domxref("SubtleCrypto.deriveBits()")}}