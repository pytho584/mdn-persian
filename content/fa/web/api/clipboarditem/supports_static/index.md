---
title: "ClipboardItem: supports() static method"
short-title: supports()
slug: Web/API/ClipboardItem/supports_static
page-type: web-api-static-method
browser-compat: api.ClipboardItem.supports_static
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

متد ایستای **`supports()`** از رابط {{domxref("ClipboardItem")}} مقدار `true` را برمی‌گرداند اگر {{Glossary("MIME type")}} داده شده توسط کلیپ‌بورد پشتیبانی شود، و در غیر این صورت `false`.

توجه داشته باشید که [Clipboard API](/en-US/docs/Web/API/Clipboard_API) پشتیبانی از متن ساده، HTML و فایل‌های PNG را الزامی می‌کند. متد `supports()` همیشه برای این نوع MIME ها مقدار `true` برمی‌گرداند، بنابراین آزمایش آن‌ها ضروری نیست.

## نحو

```js-nolint
supports(type)
```

### پارامترها

- `type`
  - : یک رشته (string) که {{Glossary("MIME type")}} مورد آزمایش را مشخص می‌کند.

    این نوع MIME ها همیشه پشتیبانی می‌شوند:
    - `text/plain`
    - `text/html`
    - `image/png`

    این نوع MIME ها ممکن است پشتیبانی شوند:
    - `image/svg+xml`
    - فرمت‌های نوع MIME سفارشی که با `"web "` شروع می‌شوند.
      نوع سفارشی (بدون پیشوند `"web "`) باید قالب‌بندی صحیح برای یک نوع MIME داشته باشد.

### مقدار بازگشتی

`true` اگر {{Glossary("MIME type")}} داده شده توسط کلیپ‌بورد پشتیبانی شود، در غیر این صورت `false`.

## مثال‌ها

### نوشتن یک تصویر در کلیپ‌بورد

مثال زیر یک تصویر SVG را دریافت می‌کند، آن را به صورت یک {{domxref("Blob")}} نمایش می‌دهد و سپس آن را در کلیپ‌بورد می‌نویسد.

ما از `supports()` استفاده می‌کنیم تا قبل از دریافت تصویر و نوشتن آن با استفاده از {{domxref("clipboard.write()")}} بررسی کنیم که آیا نوع MIME `"image/svg+xml"` توسط کلیپ‌بورد پشتیبانی می‌شود یا خیر. همچنین کل بدنه تابع را در یک عبارت [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) قرار می‌دهیم تا هر خطای دیگری، مانند عدم پشتیبانی از خود `ClipboardItem`، را بگیریم.

```js
async function writeClipImg() {
  try {
    if (ClipboardItem.supports("image/svg+xml")) {
      const imgURL = "/my-image.svg";
      const data = await fetch(imgURL);
      const blob = await data.blob();
      await navigator.clipboard.write([
        new ClipboardItem({
          [blob.type]: blob,
        }),
      ]);
      console.log("Fetched image copied to clipboard.");
    } else {
      console.log("SVG image not supported by clipboard");
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [مقاله پشتیبانی از تصویر برای کلیپ‌بورد ناهمگام](https://web.dev/articles/async-clipboard)