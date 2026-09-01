---
title: "Element: beforescriptexecute event"
short-title: beforescriptexecute
slug: Web/API/Element/beforescriptexecute_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.Element.beforescriptexecute_event
---

{{APIRef("DOM")}}{{Non-standard_header}}{{deprecated_header}}

> [!WARNING]
> این رویداد در یک نسخهٔ اولیهٔ مشخصات به‌عنوان پیشنهاد مطرح شده بود. به آن تکیه نکنید.

رویداد **`beforescriptexecute`** زمانی که یک اسکریپت در آستانهٔ اجرا قرار دارد، فعال می‌شود. لغو کردن این رویداد از اجرای اسکریپت جلوگیری می‌کند.

این یک رویداد اختصاصی مربوط به Gecko (فایرفاکس) است.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("beforescriptexecute", (event) => { })

onbeforescriptexecute = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مشخصات

بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`afterscriptexecute`](/en-US/docs/Web/API/Element/afterscriptexecute_event)