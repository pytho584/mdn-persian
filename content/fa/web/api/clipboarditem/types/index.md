---
title: "ClipboardItem: types property"
short-title: types
slug: Web/API/ClipboardItem/types
page-type: web-api-instance-property
browser-compat: api.ClipboardItem.types
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

ویژگی فقط‑خواندنی **`types`** از رابط {{domxref("ClipboardItem")}} یک {{jsxref("Array")}} از {{Glossary("MIME type", 'انواع MIME')}} موجود در {{domxref("ClipboardItem")}} را برمی‌گرداند.

## مقدار

یک {{jsxref("Array")}} از {{Glossary("MIME type", 'انواع MIME')}} موجود.

## مثال‌ها

در مثال زیر، تمام آیتم‌های موجود در کلیپ‌بورد را با استفاده از متد {{domxref("Clipboard.read()")}} دریافت می‌کنیم، سپس ویژگی `types` را برای یافتن انواع موجود بررسی می‌کنیم و پیش از استفاده از متد {{domxref("ClipboardItem.getType()")}} برای بازگرداندن هر آیتم داده به صورت یک {{domxref("Blob")}}، این کار را انجام می‌دهیم. اگر محتوای کلیپ‌بوردی برای نوع مشخص‌شده یافت نشود، یک خطا بازگردانده می‌شود.

```js
async function getClipboardContents() {
  try {
    const clipboardItems = await navigator.clipboard.read();

    for (const clipboardItem of clipboardItems) {
      for (const type of clipboardItem.types) {
        const blob = await clipboardItem.getType(type);
        // we can now use blob here
      }
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
- [Image support for Async Clipboard article](https://web.dev/articles/async-clipboard)