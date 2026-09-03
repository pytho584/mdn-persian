---
title: "OffscreenCanvas: convertToBlob() method"
short-title: convertToBlob()
slug: Web/API/OffscreenCanvas/convertToBlob
page-type: web-api-instance-method
browser-compat: api.OffscreenCanvas.convertToBlob
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`OffscreenCanvas.convertToBlob()`** یک شیء {{domxref("Blob")}} می‌سازد که تصویر موجود در بوم (canvas) را نمایش می‌دهد.

قالب فایل دلخواه و کیفیت تصویر را می‌توان مشخص کرد.
اگر قالب فایل مشخص نشود، یا اگر قالب داده‌شده پشتیبانی نشود، داده‌ها به صورت `image/png` خروجی گرفته می‌شوند.
مرورگرها موظف به پشتیبانی از `image/png` هستند؛ بسیاری از آن‌ها از قالب‌های اضافی مانند `image/jpeg` و `image/webp` نیز پشتیبانی می‌کنند.

تصویر ایجادشده برای قالب‌های فایلی که از ذخیره‌سازی فراداده‌های وضوح تصویر پشتیبانی می‌کنند، وضوحی برابر با ۹۶dpi خواهد داشت.

## نحو (Syntax)

```js-nolint
convertToBlob()
convertToBlob(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `type`
      - : رشته‌ای که قالب تصویر را مشخص می‌کند.
        نوع پیش‌فرض `image/png` است؛ اگر نوع مشخص‌شده پشتیبانی نشود نیز از همین قالب استفاده خواهد شد.
    - `quality`
      - : یک {{jsxref("Number")}} بین `0` و `1` که کیفیت تصویر را هنگام ایجاد تصاویر با استفاده از قالب‌های فایل دارای فشرده‌سازی اتلافی (مانند `image/jpeg` یا `image/webp`) مشخص می‌کند.
        اگر این گزینه مشخص نشود، یا اگر عدد خارج از بازه مجاز باشد، عامل کاربر (user agent) از مقدار کیفیت پیش‌فرض خود استفاده می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که یک شیء {{domxref("Blob")}} بازمی‌گرداند و تصویر موجود در بوم را نمایش می‌دهد.

### استثناها (Exceptions)

ممکن است promise با استثناهای زیر رد شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : شیء `OffscreenCanvas` جدا (detached) نشده است؛ به عبارت دیگر همچنان با DOM مرتبط است و با worker فعلی مرتبط نیست.

- `SecurityError` {{domxref("DOMException")}}
  - : حالت بافت (context mode) بوم 2d است و نقشه بیت (bitmap) دارای مبدا پاک (origin-clean) نیست؛ دست‌کم بخشی از محتوای آن از سایتی غیر از سایتی که خود سند از آن بارگذاری شده، بارگذاری شده یا ممکن است بارگذاری شده باشد.

- `IndexSizeError` {{domxref("DOMException")}}
  - : نقشه بیت بوم هیچ پیکسلی ندارد (یا بُعد افقی یا عمودی آن صفر است).

- `EncodingError` {{domxref("DOMException")}}
  - : به دلیل خطای رمزگذاری، امکان ایجاد blob وجود نداشت.

## مثال‌ها

```js
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// Perform some drawing using the gl context

offscreen.convertToBlob().then((blob) => console.log(blob));
// Blob { size: 334, type: "image/png" }
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد، {{domxref("OffscreenCanvas")}}.