---
title: "Notification: navigate property"
short-title: navigate
slug: Web/API/Notification/navigate
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Notification.navigate
---

{{APIRef("Web Notifications")}}{{securecontext_header}}{{SeeCompatTable}} {{AvailableInWorkers}}

خصوصیت فقط‌خواندنی **`navigate`** در رابط {{domxref("Notification")}} شامل نشانی اینترنتی (URL) است که عامل کاربر (user agent) هنگام فعال‌سازی اعلان توسط کاربر به آن هدایت می‌شود.

این مقدارِ حل‌شدهٔ URLای است (در صورت وجود) که در گزینهٔ `navigate` سازندهٔ {{domxref("Notification.Notification", "Notification()")}} یا متد {{domxref("ServiceWorkerRegistration.showNotification()")}} مشخص شده است.

به‌طور معمول، فعال‌سازی یک اعلان غیرماندگار (non-persistent) رویداد {{domxref("Notification.click_event", "click")}} را روی شیء {{domxref("Notification")}} آن، و فعال‌سازی یک اعلان ماندگار (persistent) رویداد {{domxref("ServiceWorkerGlobalScope.notificationclick_event", "notificationclick")}} را روی {{domxref("ServiceWorkerGlobalScope")}} آغاز می‌کند.

هنگامی که کاربر یک اعلان دارای URL ناوبری را فعال می‌کند، عامل کاربر به جای ایجاد هر یک از این رویدادها، به URL مشخص‌شده هدایت می‌شود. این امکان را می‌دهد که اعلان‌ها کاربران را بدون نیاز به یک کنترل‌کنندهٔ رویداد (event handler) به یک صفحهٔ خاص هدایت کنند.

## مقدار

یک رشته شامل یک {{glossary("URL")}}، یا یک رشتهٔ خالی اگر URL ناوبری تنظیم نشده باشد.

## مثال‌ها

### خواندن مقدار خصوصیت navigate

خصوصیت `navigate` وقتی URL ناوبری تنظیم شده باشد، رشتهٔ URL حل‌شده را برمی‌گرداند، در غیر این صورت یک رشتهٔ خالی.

```js
const notification = new Notification("پیام جدید از مریم", {
  body: "سلام، برای ناهار وقت داری؟",
  navigate: "/messages/maryam",
});

// خصوصیت شامل URL مطلق حل‌شده است
console.log(notification.navigate); // به‌عنوان مثال: "https://example.com/messages/maryam"

// بدون گزینهٔ navigate، خصوصیت یک رشتهٔ خالی است
const basic = new Notification("سلام!");
console.log(basic.navigate); // ""
```

### استفاده از navigate با یک کارگر سرویس (service worker)

هنگام استفاده از اعلان‌های ماندگار از طریق یک کارگر سرویس، گزینهٔ `navigate` به اعلان اجازه می‌دهد که هنگام فعال‌سازی صفحه‌ای را باز کند، بدون نیاز به مدیریت رویداد {{domxref("ServiceWorkerGlobalScope.notificationclick_event", "notificationclick")}}.

```js
// داخل یک کارگر سرویس
self.registration.showNotification("سفارش ارسال شد!", {
  body: "سفارش شماره ۱۲۳۴ شما ارسال شده است.",
  navigate: "/orders/1234",
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API Notifications](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)
- سازندهٔ {{domxref("Notification.Notification", "Notification()")}}
- {{domxref("ServiceWorkerRegistration.showNotification()")}}