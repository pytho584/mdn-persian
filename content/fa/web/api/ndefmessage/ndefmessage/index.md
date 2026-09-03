---
title: "NDEFMessage: NDEFMessage() constructor"
short-title: NDEFMessage()
slug: Web/API/NDEFMessage/NDEFMessage
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.NDEFMessage.NDEFMessage
---

{{SecureContext_Header}}{{APIRef("Web NFC API")}}{{SeeCompatTable}}

سازنده‌ی **`NDEFMessage()`** یک شیء جدید {{domxref("NDEFMessage")}} ایجاد می‌کند که با رکوردهای NDEF داده شده مقداردهی اولیه می‌شود.

## Syntax

```js-nolint
new NDEFMessage(records)
```

### Parameters

- `records`
  - : آرایه‌ای از اشیاء با اعضای زیر:
    - `data` {{optional_inline}}
      - : شامل داده‌ای است که باید ارسال شود؛ یکی از یک رشته (string)، یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}}، یا یک آرایه از رکوردهای تو در تو.
    - `encoding` {{optional_inline}}
      - : رشته‌ای که encoding رکورد را مشخص می‌کند.
    - `id` {{optional_inline}}
      - : یک شناسه تعریف‌شده توسط توسعه‌دهنده برای رکورد.
    - `lang` {{optional_inline}}
      - : یک {{glossary("BCP 47 language tag")}} معتبر.
    - `mediaType` {{optional_inline}}
      - : یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
    - `recordType`
      - : رشته‌ای که نوع داده‌های ذخیره‌شده در `data` را نشان می‌دهد. باید یکی از مقادیر زیر باشد:
        - `"absolute-url"`
          - : یک URL مطلق به داده.
        - `"empty"`
          - : یک {{domxref("NDEFRecord")}} خالی.
        - `"mime"`
          - : یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
        - `"smart-poster"`
          - : یک پوستر هوشمند (smart poster) مطابق تعریف مشخصات [NDEF-SMARTPOSTER](https://w3c.github.io/web-nfc/#bib-ndef-smartposter).
        - `"text"`
          - : متن مطابق تعریف مشخصات [NDEF-TEXT](https://w3c.github.io/web-nfc/#bib-ndef-text).
        - `"unknown"`
          - : نوع رکورد ناشناخته است.
        - `"URL"`
          - : یک URL مطابق تعریف مشخصات [NDEF-URI](https://w3c.github.io/web-nfc/#bib-ndef-uri).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}