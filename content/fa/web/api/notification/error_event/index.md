---
title: "Notification: error event"
short-title: error
slug: Web/API/Notification/error_event
page-type: web-api-event
browser-compat: api.Notification.error_event
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

رویداد **`error`** از رابط {{domxref("Notification")}} زمانی رخ می‌دهد که مشکلی برای یک {{domxref("Notification")}} پیش بیاید (در بسیاری از موارد، خطایی که از نمایش اعلان جلوگیری می‌کند).

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)