---
title: "Notification: click event"
short-title: click
slug: Web/API/Notification/click_event
page-type: web-api-event
browser-compat: api.Notification.click_event
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

رویداد **`click`** در رابط {{domxref("Notification")}} زمانی رخ می‌دهد که کاربر روی {{domxref("Notification")}} نمایش داده‌شده کلیک کند.

رفتار پیش‌فرض این است که تمرکز به نمای (viewport) بافت مرورگرِ مرتبط با اعلان منتقل شود. اگر این رفتار را نمی‌خواهید، متد {{domxref("Event/preventDefault", "preventDefault()")}} را روی شیء رویداد فراخوانی کنید.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("click", (event) => { })

onclick = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

در مثال زیر، از یک handler با نام `onclick` استفاده می‌کنیم تا پس از کلیک روی اعلان، یک صفحه وب را در یک تب جدید باز کنیم (با استفاده از پارامتر `'_blank'`):

```js
notification.onclick = (event) => {
  event.preventDefault(); // جلوگیری از متمرکز شدن مرورگر روی تب اعلان
  window.open("https://www.mozilla.org", "_blank");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)