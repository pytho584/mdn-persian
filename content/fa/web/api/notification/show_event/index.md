---
title: "Notification: show event"
short-title: show
slug: Web/API/Notification/show_event
page-type: web-api-event
browser-compat: api.Notification.show_event
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

رویداد **`show`** از رابط {{domxref("Notification")}} زمانی رخ می‌دهد که یک {{domxref("Notification")}} نمایش داده می‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد را تنظیم نمایید.

```js-nolint
addEventListener("show", (event) => { })

onshow = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)