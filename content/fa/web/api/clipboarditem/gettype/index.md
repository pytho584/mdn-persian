---
title: "ClipboardItem: getType() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ClipboardItem/getType"
---

---
title: "ClipboardItem: getType() method"
short-title: getType()
slug: Web/API/ClipboardItem/getType
page-type: web-api-instance-method
browser-compat: api.ClipboardItem.getType
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

متد **`getType()`** در رابط {{domxref("ClipboardItem")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{domxref("Blob")}} از نوع {{Glossary("MIME type")}} درخواستی حل می‌شود، یا در صورت یافت نشدن نوع MIME، یک خطا برمی‌گرداند.

## نحو (Syntax)

```js-nolint
getType(type)
```

### پارامترها

- `type`
  - : یک {{Glossary("MIME type")}} معتبر.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء {{domxref("Blob")}} حل می‌شود.

### استثناها (Exceptions)

- `NotFoundError` {{domxref("DOMException")}}
  - : `type` با هیچ {{Glossary("MIME type")}} شناخته‌شده‌ای مطابقت ندارد.
- {{jsxref("TypeError")}}
  - : هیچ پارامتری مشخص نشده است یا `type` مربوط به {{domxref("ClipboardItem")}} نیست.

## مثال‌ها

در مثال زیر، تمام آیتم‌های کلیپ‌بورد را از طریق متد {{domxref("clipboard.read()")}} برمی‌گردانیم. برای هر آیتم، ویژگی {{domxref("ClipboardItem.types")}} را به متد `getType()` پاس می‌دهیم که شیء `Blob` مربوطه را برمی‌گرداند.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [Image support for Async Clipboard article](https://web.dev/articles/async-clipboard)