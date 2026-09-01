---
title: EcKeyImportParams
slug: Web/API/EcKeyImportParams
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#dfn-EcKeyImportParams
---

{{ APIRef("Web Crypto API") }}

دیکشنری **`EcKeyImportParams`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) نمایانگر شیئی است که باید به عنوان پارامتر `algorithm` به متدهای {{domxref("SubtleCrypto.importKey()")}} یا {{domxref("SubtleCrypto.unwrapKey()")}} ارسال شود، هنگام تولید هر جفت‌کلید مبتنی بر منحنی بیضوی: یعنی زمانی که الگوریتم به عنوان یکی از [ECDSA](/en-US/docs/Web/API/SubtleCrypto/sign#ecdsa) یا [ECDH](/en-US/docs/Web/API/SubtleCrypto/deriveKey#ecdh) شناسایی شود.

## ویژگی‌های نمونه

- `name`
  - : یک رشته. این باید به `ECDSA` یا `ECDH` تنظیم شود، بسته به الگوریتمی که می‌خواهید استفاده کنید.
- `namedCurve`
  - : یک رشته که نام منحنی بیضوی مورد استفاده را نشان می‌دهد. این می‌تواند یکی از نام‌های زیر برای منحنی‌های تأیید شده توسط [NIST](https://www.nist.gov/) باشد:
    - `P-256`
    - `P-384`
    - `P-521`

## مثال‌ها

مثال‌های مربوط به {{domxref("SubtleCrypto.importKey()")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

مرورگرهایی که از الگوریتم‌های "ECDH" یا "ECDSA" برای متدهای {{domxref("SubtleCrypto.importKey()")}} یا {{domxref("SubtleCrypto.wrapKey()")}} پشتیبانی می‌کنند، از این نوع پشتیبانی خواهند کرد.

## همچنین ببینید

- {{domxref("SubtleCrypto.importKey()")}}
- {{domxref("SubtleCrypto.unwrapKey()")}}