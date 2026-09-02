---
title: "ImageDecoder: ImageDecoder() constructor"
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

سازنده `ImageDecoder()` یک شیء جدید از نوع {{domxref("ImageDecoder")}} ایجاد می‌کند که داده‌های تصویر را باز کرده و رمزگشایی می‌کند.

## نحو

```js-nolint
new ImageDecoder(init)
```

### پارامترها

- `init`
  - : یک شیء حاوی اعضای زیر:
    - `type`
      - : یک رشته حاوی [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) فایل تصویری که قرار است رمزگشایی شود.
    - `data`
      - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}}، یا یک {{domxref("ReadableStream")}} از بایت‌ها که یک نوع تصویر رمزگذاری شده را مطابق با `type` نشان می‌دهد.
    - `premultiplyAlpha` {{optional_inline}}
      - : مشخص می‌کند که آیا کانال‌های رنگی تصویر رمزگشایی شده باید توسط کانال آلفا پیش‌ضرب شوند. اگر ارائه نشود، به عنوان `"default"` تنظیم می‌شود:
        - `"none"`
        - `"premultiply"`
        - `"default"`
    - `colorSpaceConversion` {{optional_inline}}
      - : مشخص می‌کند که آیا تصویر باید با استفاده از تبدیل فضای رنگی رمزگشایی شود. اگر ارائه نشود، به عنوان `"default"` تنظیم می‌شود. مقدار `"default"` نشان می‌دهد که رفتار خاص پیاده‌سازی استفاده می‌شود:
        - `"none"`
        - `"default"`
    - `desiredWidth` {{optional_inline}}
      - : یک عدد صحیح که عرض مورد نظر برای خروجی رمزگشایی شده را نشان می‌دهد. تأثیری ندارد مگر اینکه کدک تصویر از رمزگشایی با وضوح متغیر پشتیبانی کند.
    - `desiredHeight` {{optional_inline}}
      - : یک عدد صحیح که ارتفاع مورد نظر برای خروجی رمزگشایی شده را نشان می‌دهد. تأثیری ندارد مگر اینکه کدک تصویر از رمزگشایی با وضوح متغیر پشتیبانی کند.
    - `preferAnimation` {{optional_inline}}
      - : یک {{jsxref("Boolean")}} که نشان می‌دهد آیا انتخاب اولیه مسیر باید یک مسیر متحرک را ترجیح دهد.
    - `transfer`
      - : آرایه‌ای از {{jsxref("ArrayBuffer")}}ها که `ImageDecoder` آن‌ها را جدا کرده و مالکیت آن‌ها را به دست می‌گیرد. اگر آرایه شامل {{jsxref("ArrayBuffer")}} پشتیبان `data` باشد، `ImageDecoder` به جای کپی کردن از آن، مستقیماً از آن بافر استفاده می‌کند.

## مثال‌ها

مثال زیر یک `ImageDecoder` جدید با گزینه‌های مورد نیاز ایجاد می‌کند.

```js
let init = {
  type: "image/png",
  data: imageByteStream,
};

let imageDecoder = new ImageDecoder(init);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}