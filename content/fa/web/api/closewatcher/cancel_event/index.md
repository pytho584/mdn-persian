---
title: "CloseWatcher: cancel event"
slug: Web/API/CloseWatcher/cancel_event
page-type: web-api-event
browser-compat: api.CloseWatcher.cancel_event
---

{{APIRef("HTML DOM")}}

رویداد `cancel` قبل از رویداد `close` روی یک شیء {{domxref("CloseWatcher")}} پرتاب می‌شود، تا در صورت لزوم بتوان از پرتاب شدن `close` جلوگیری کرد. این رویداد توسط تمام سیگنال‌های بستن (مثلاً کلید <kbd>Esc</kbd>) و همچنین {{domxref("CloseWatcher.requestClose()")}} ایجاد می‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("cancel", (event) => { })

oncancel = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مثال‌ها

### استفاده از رویداد `cancel`

در این مثال، از کاربر می‌خواهیم تأیید کند که واقعاً می‌خواهد مؤلفه را ببندد، و اگر نخواست، رویداد را با استفاده از {{domxref("Event.preventDefault()")}} لغو می‌کنیم، که از پرتاب شدن رویداد `close` جلوگیری می‌کند.

```js
watcher.addEventListener("cancel", (e) => {
  if (e.cancelable && hasUnsavedData) {
    const userReallyWantsToClose = confirm("Are you sure you want to close?");
    if (!userReallyWantsToClose) {
      e.preventDefault();
    }
  }
});

// Trigger a close request manually
watcher.requestClose();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}