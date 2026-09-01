---
title: "EcKeyGenParams"
---

---
title: EcKeyGenParams
slug: Web/API/EcKeyGenParams
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-EcKeyGenParams
---

{{ APIRef("Web Crypto API") }}

دیکشنری **`EcKeyGenParams`** در [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) نشان‌دهندهٔ شیئی است که هنگام تولید هر جفت‌کلید مبتنی بر منحنی بیضوی باید به‌عنوان پارامتر `algorithm` به {{domxref("SubtleCrypto.generateKey()")}} ارسال شود؛ یعنی زمانی که الگوریتم به‌صورت [ECDSA](/en-US/docs/Web/API/SubtleCrypto/sign#ecdsa) یا [ECDH](/en-US/docs/Web/API/SubtleCrypto/deriveKey#ecdh) شناسایی شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. این مقدار باید بسته به الگوریتمی که می‌خواهید استفاده کنید، روی `ECDSA` یا `ECDH` تنظیم شود.
- `namedCurve`
  - : یک رشته که نام منحنی بیضوی مورد استفاده را نشان می‌دهد. این مقدار می‌تواند یکی از نام‌های زیر برای منحنی‌های تأییدشده توسط [NIST](https://www.nist.gov/) باشد:
    - `P-256`
    - `P-384`
    - `P-521`

## مثال‌ها

نمونه‌ها را در صفحهٔ {{domxref("SubtleCrypto.generateKey()")}} ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

مرورگرهایی که از الگوریتم‌های «ECDH» یا «ECDSA» برای متد {{domxref("SubtleCrypto.generateKey()")}} پشتیبانی می‌کنند، از این نوع نیز پشتیبانی خواهند کرد.

## جستارهای وابسته

- {{domxref("SubtleCrypto.generateKey()")}}.