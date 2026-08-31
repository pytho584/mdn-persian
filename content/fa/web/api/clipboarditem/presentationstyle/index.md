---
title: "ClipboardItem: presentationStyle property"
short-title: presentationStyle
slug: Web/API/ClipboardItem/presentationStyle
page-type: web-api-instance-property
browser-compat: api.ClipboardItem.presentationStyle
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

ویژگی فقط‌خواندنی **`presentationStyle`** از رابط {{domxref("ClipboardItem")}} رشته‌ای را برمی‌گرداند که نشان می‌دهد یک مورد باید چگونه نمایش داده شود.

به‌عنوان مثال، در برخی زمینه‌ها یک تصویر ممکن است به‌صورت درون‌خطی (inline) نمایش داده شود، در حالی که در برخی دیگر ممکن است به‌صورت پیوست (attachment) ارائه شود.

## مقدار

این مقدار یکی از موارد `"unspecified"`، `"inline"` یا `"attachment"` است.

## مثال‌ها

در مثال زیر، همه موارد موجود در کلیپ‌برد را از طریق متد {{domxref("clipboard.read()")}} برمی‌گردانیم و سپس ویژگی `presentationStyle` را در کنسول ثبت (log) می‌کنیم.

```js
async function getClipboardContents() {
  try {
    const clipboardItems = await navigator.clipboard.read();

    for (const clipboardItem of clipboardItems) {
      console.log(clipboardItem.presentationStyle);
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [Image support for Async Clipboard article](https://web.dev/articles/async-clipboard)