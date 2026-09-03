```yaml
---
title: "Notification: maxActions static property"
short-title: maxActions
slug: Web/API/Notification/maxActions_static
page-type: web-api-static-property
browser-compat: api.Notification.maxActions_static
---

{{APIRef("Web Notifications")}}{{SecureContext_Header}} {{AvailableInWorkers}}

خاصیت **`maxActions`** (ایستا و فقط-خواندنی) از رابط {{domxref("Notification")}} حداکثر تعداد اقداماتی را که می‌توانند در یک اعلان نمایش داده شوند، برمی‌گرداند.

## مقدار

یک عدد صحیح.

## توضیحات

اقدامات اعلان، دکمه‌ها یا کنترل‌هایی هستند که درون [اعلان‌های پایدار](/en-US/docs/Web/API/Notifications_API#persistent_and_non-persistent_notifications) ظاهر می‌شوند. این اقدامات با استفاده از گزینه [`actions`](/en-US/docs/Web/API/ServiceWorkerRegistration/showNotification#actions) آرگومان دوم متد {{domxref("ServiceWorkerRegistration.showNotification", "showNotification()")}} تنظیم می‌شوند.

مرورگرها معمولاً حداکثر تعداد اقداماتی را که برای یک اعلان خاص نمایش می‌دهند، محدود می‌کنند. خاصیت `maxActions` این محدودیت را بازمی‌گرداند؛ یعنی بیشینه تعداد عناصری در آرایه {{domxref("Notification.actions")}} که توسط عامل کاربر رعایت خواهد شد.

## مثال‌ها

### ثبت حداکثر تعداد ممکن اقدامات

قطعه کد زیر حداکثر تعداد اقدامات پشتیبانی‌شده را ثبت می‌کند.

```js
const maxActions = Notification.maxActions;
console.log(
  `این دستگاه می‌تواند حداکثر ${maxActions} اقدام را روی هر اعلان نمایش دهد.`,
);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)
- {{domxref("Notification.actions")}}
```