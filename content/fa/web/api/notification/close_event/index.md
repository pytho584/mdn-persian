---
title: "Notification: close event"
short-title: close
slug: Web/API/Notification/close_event
page-type: web-api-event
browser-compat: api.Notification.close_event
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

رویداد **`close`** از رابط {{domxref("Notification")}} زمانی رخ می‌دهد که یک {{domxref("Notification")}} بسته می‌شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگی مدیریت رویداد (event handler property) می‌توانید به صورت زیر عمل کنید:

```js-nolint
addEventListener("close", (event) => { })

onclose = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)