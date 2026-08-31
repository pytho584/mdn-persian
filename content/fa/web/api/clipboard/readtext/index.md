---
title: "Clipboard: readText() method"
---

---
title: "Clipboard: readText() method"
short-title: readText()
slug: Web/API/Clipboard/readText
page-type: web-api-instance-method
browser-compat: api.Clipboard.readText
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

متد **`readText()`** از رابط {{domxref("Clipboard")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک کپی از محتوای متنی کلیپ‌برد سیستم تکمیل می‌شود.

> [!NOTE]
> برای خواندن محتوای غیرمتنی از کلیپ‌برد، به جای آن از متد {{domxref("Clipboard.read", "read()")}} استفاده کنید.
> می‌توانید متن را با استفاده از {{domxref("Clipboard.writeText", "writeText()")}} در کلیپ‌برد بنویسید.

## نحو (Syntax)

```js-nolint
readText()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک رشته شامل محتوای متنی کلیپ‌برد resolve می‌شود.

اگر کلیپ‌برد خالی باشد، حاوی متن نباشد، یا در میان اشیاء نشان‌دهنده محتویات کلیپ‌برد، یک نمایش متنی نداشته باشد، یک رشته خالی برمی‌گرداند.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر دسترسی برای خواندن کلیپ‌برد مجاز نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر کلیپ‌برد نشان دهد که حاوی داده‌هایی است که می‌توانند به صورت متن نمایش داده شوند، اما قادر به ارائه یک نمایش متنی نباشد، پرتاب می‌شود.

## ملاحظات امنیتی

خواندن از کلیپ‌برد فقط در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) قابل انجام است.

نیازمندی‌های امنیتی اضافی در بخش [ملاحظات امنیتی](/en-US/docs/Web/API/Clipboard_API#security_considerations) از نمای کلی API پوشش داده شده‌اند.

## مثال‌ها

این مثال محتویات متنی کلیپ‌برد را بازیابی کرده و متن برگشتی را در محتویات یک عنصر انتخاب شده درج می‌کند.

```js
const destination = document.getElementById("outbox");
destinationImage.addEventListener("click", () => {
  navigator.clipboard
    .readText()
    .then((clipText) => (destination.innerText = clipText));
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [پشتیبانی از تصویر برای مقاله کلیپ‌برد ناهمگام](https://web.dev/articles/async-clipboard)
- {{domxref("Clipboard.read()")}}
- {{domxref("Clipboard.writeText()")}}
- {{domxref("Clipboard.write()")}}