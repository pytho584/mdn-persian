---
title: "Clipboard: writeText() method"
short-title: writeText()
slug: Web/API/Clipboard/writeText
page-type: web-api-instance-method
browser-compat: api.Clipboard.writeText
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

متد **`writeText()`** از رابط {{domxref("Clipboard")}} متن مشخص‌شده را در کلیپ‌بورد سیستم می‌نویسد و یک {{jsxref("Promise")}} برمی‌گرداند که پس از به‌روزرسانی کلیپ‌بورد سیستم، resolved می‌شود.

## Syntax

```js-nolint
writeText(newClipText)
```

### Parameters

- `newClipText`
  - : رشته‌ای که باید در کلیپ‌بورد نوشته شود.

### Return value

یک {{jsxref("Promise")}} که پس از به‌روزرسانی محتویات کلیپ‌بورد resolved می‌شود.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر نوشتن در کلیپ‌بورد مجاز نباشد، پرتاب می‌شود.

## ملاحظات امنیتی

نوشتن در کلیپ‌بورد فقط در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) امکان‌پذیر است.

الزامات امنیتی اضافی در بخش [ملاحظات امنیتی](/en-US/docs/Web/API/Clipboard_API#security_considerations) از نمای کلی API پوشش داده شده است.

## مثال‌ها

این مثال محتویات کلیپ‌بورد را روی رشته "\<empty clipboard>" تنظیم می‌کند.

```js
button.addEventListener("click", () => writeClipboardText("<empty clipboard>"));

async function writeClipboardText(text) {
  try {
    await navigator.clipboard.writeText(text);
  } catch (error) {
    console.error(error.message);
  }
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [Image support for Async Clipboard article](https://web.dev/articles/async-clipboard)
- {{domxref("Clipboard.write()")}}
- {{domxref("Clipboard.read()")}}
- {{domxref("Clipboard.readText()")}}