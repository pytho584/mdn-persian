---
title: "NDEFRecord: NDEFRecord() constructor"
short-title: NDEFRecord()
slug: Web/API/NDEFRecord/NDEFRecord
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.NDEFRecord.NDEFRecord
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

سازندهٔ **`NDEFRecord()`** از [Web NFC API](/en-US/docs/Web/API/Web_NFC_API) یک شیء تازه‌ساختهٔ {{DOMxRef("NDEFRecord")}} برمی‌گرداند که داده‌هایی را نمایانگر است که می‌توان از دستگاه‌های NFC سازگار (مثلاً تگ‌های NFC پشتیبان NDEF) خواند یا روی آن‌ها نوشت.

## سینتکس

```js-nolint
new NDEFRecord(options)
```

### پارامترها

- `options`
  - : یک شیء با ویژگی‌های زیر:
    - `data` {{optional_inline}}
      - : شامل داده‌هایی است که قرار است ارسال شوند. این مقدار می‌تواند یک رشته، یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}}، یا آرایه‌ای از رکوردهای تودرتو باشد.
    - `encoding` {{optional_inline}}
      - : رشته‌ای که رمزگذاری رکورد را مشخص می‌کند.
    - `id` {{optional_inline}}
      - : یک شناسهٔ تعریف‌شده توسط توسعه‌دهنده برای رکورد.
    - `lang` {{optional_inline}}
      - : یک {{glossary("BCP 47 language tag")}} معتبر.
    - `mediaType` {{optional_inline}}
      - : یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
    - `recordType`
      - : رشته‌ای که نوع دادهٔ ذخیره‌شده در `data` را نشان می‌دهد. باید یکی از مقادیر زیر باشد:
        - `"absolute-url"`
          - : یک URL مطلق که به داده اشاره می‌کند.
        - `"empty"`
          - : یک {{domxref("NDEFRecord")}} خالی.
        - `"mime"`
          - : یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
        - `"smart-poster"`
          - : یک پوستر هوشمند (smart poster) مطابق تعریف مشخصات [NDEF-SMARTPOSTER](https://w3c.github.io/web-nfc/#bib-ndef-smartposter).
        - `"text"`
          - : متن مطابق تعریف مشخصات [NDEF-TEXT](https://w3c.github.io/web-nfc/#bib-ndef-text).
        - `"unknown"`
          - : نوع رکورد شناخته‌شده نیست.
        - `"URL"`
          - : یک URL مطابق تعریف مشخصات [NDEF-URI](https://w3c.github.io/web-nfc/#bib-ndef-uri).

### مقدار بازگشتی

یک {{DOMxRef("NDEFRecord")}} جدید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}