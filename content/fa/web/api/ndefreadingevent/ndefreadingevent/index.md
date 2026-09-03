---
title: "NDEFReadingEvent: NDEFReadingEvent() constructor"
short-title: NDEFReadingEvent()
slug: Web/API/NDEFReadingEvent/NDEFReadingEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.NDEFReadingEvent.NDEFReadingEvent
---

{{APIRef("Web NFC API")}}{{securecontext_header}}{{SeeCompatTable}}

سازنده‌ی **`NDEFReadingEvent()`** یک شیء جدید از نوع {{domxref("NDEFReadingEvent")}} می‌سازد که رویدادهای ارسال‌شده در خوانش‌های جدید NFC را که توسط {{DOMxRef("NDEFReader")}} به دست می‌آیند، نشان می‌دهد.

## نحو (Syntax)

```js-nolint
new NDEFReadingEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد.
    این رشته به بزرگی/کوچکی حروف حساس است و مرورگرها همواره آن را روی `"reading"` قرار می‌دهند.
- `options`
  - : شیءای که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `serialNumber` {{optional_inline}}
      - : شماره سریال دستگاهی که پیام از آن خوانده شده است. مقدار پیش‌فرض آن `""` است و می‌توان آن را روی `null` نیز تنظیم کرد.
    - `message`
      - : شیءای با اعضای زیر:
        - `data` {{optional_inline}}
          - : حاوی داده‌ای است که قرار است ارسال شود. می‌تواند یک رشته، یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}} یا آرایه‌ای از رکوردهای تودرتو باشد.
        - `encoding` {{optional_inline}}
          - : رشته‌ای که رمزگذاری (encoding) رکورد را مشخص می‌کند.
        - `id` {{optional_inline}}
          - : شناسه‌ای تعریف‌شده توسط توسعه‌دهنده برای رکورد.
        - `lang` {{optional_inline}}
          - : یک {{glossary("BCP 47 language tag")}} معتبر.
        - `mediaType` {{optional_inline}}
          - : یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
        - `recordType`
          - : رشته‌ای که نوع داده ذخیره‌شده در `data` را نشان می‌دهد. باید یکی از مقادیر زیر باشد:
            - `"absolute-url"`
              - : یک URL مطلق برای داده.
            - `"empty"`
              - : یک {{domxref("NDEFRecord")}} خالی.
            - `"mime"`
              - : یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
            - `"smart-poster"`
              - : یک پوستر هوشمند (smart poster) طبق مشخصات [NDEF-SMARTPOSTER](https://w3c.github.io/web-nfc/#bib-ndef-smartposter).
            - `"text"`
              - : متن طبق مشخصات [NDEF-TEXT](https://w3c.github.io/web-nfc/#bib-ndef-text).
            - `"unknown"`
              - : نوع رکورد مشخص نیست.
            - `"URL"`
              - : یک URL طبق مشخصات [NDEF-URI](https://w3c.github.io/web-nfc/#bib-ndef-uri).

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("NDEFReadingEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}