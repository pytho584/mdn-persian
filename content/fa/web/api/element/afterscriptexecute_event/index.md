---
title: "Element: afterscriptexecute event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/afterscriptexecute_event"
---

{{APIRef}}{{Non-standard_header}}{{deprecated_header}}

> [!WARNING]
> این رویداد در نسخه‌ای اولیه از مشخصات به‌عنوان پیشنهاد مطرح شده بود. به آن اتکا نکنید.

رویداد **`afterscriptexecute`** پس از اجرا شدن یک اسکریپت فعال می‌شود.

این یک رویداد اختصاصی مربوط به Gecko (فایرفاکس) است.

این رویداد قابل لغو (cancelable) نیست.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("afterscriptexecute", (event) => { })

onafterscriptexecute = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مشخصات

بخشی از هیچ مشخصه‌ای نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`beforescriptexecute`](/en-US/docs/Web/API/Element/beforescriptexecute_event)