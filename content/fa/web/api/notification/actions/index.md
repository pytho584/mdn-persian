---
title: "Notification: actions property"
short-title: actions
slug: Web/API/Notification/actions
page-type: web-api-instance-property
browser-compat: api.Notification.actions
---

{{APIRef("Web Notifications")}}{{SecureContext_Header}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`actions`** در رابط {{domxref("Notification")}}، اکشن‌هایی را که کاربر هنگام تعامل با اعلان امکان انتخاب آن‌ها را دارد در اختیار قرار می‌دهد.

## مقدار

یک آرایه‌ی فقط‌خواندنی از اکشن‌ها. هر عنصر از این آرایه، یک شیء با اعضای زیر است:

- `action`
  - : رشته‌ای که یک اکشن کاربر را برای نمایش روی اعلان مشخص می‌کند.
- `title`
  - : رشته‌ای شامل متنی که برای کاربر نمایش داده می‌شود.
- `icon`
  - : رشته‌ای شامل URL آیکونی که همراه با اکشن نمایش داده می‌شود.
- `navigate` {{optional_inline}} {{experimental_inline}}
  - : رشته‌ای شامل URL مقصد برای هدایت، زمانی که کاربر این اکشن را فعال می‌کند. اگر این مقدار تنظیم شده باشد، عامل کاربر به جای صدور رویداد {{domxref("ServiceWorkerGlobalScope.notificationclick_event", "notificationclick")}} به این URL هدایت می‌شود. برای اطلاعات بیشتر به {{domxref("Notification.navigate")}} مراجعه کنید.

## توضیحات

اکشن‌های اعلان، دکمه‌ها یا کنترل‌هایی هستند که درون [اعلان‌های ماندگار](/en-US/docs/Web/API/Notifications_API#persistent_and_non-persistent_notifications) نمایش داده می‌شوند. این اکشن‌ها با استفاده از گزینه‌ی [`actions`](/en-US/docs/Web/API/ServiceWorkerRegistration/showNotification#actions) در آرگومان دوم متد {{domxref("ServiceWorkerRegistration.showNotification", "showNotification()")}} تنظیم می‌شوند. توجه داشته باشید که اکشن‌ها برای اعلان‌های غیرماندگار در دسترس نیستند. اگر یک شیء `options` با ویژگی `actions` که چیزی غیر از `null` است به سازنده‌ی {{domxref("Notification/Notification", "Notification()")}} ارسال کنید، یک `TypeError` پرتاب می‌شود.

کلیک روی دکمه‌ی مربوط به هر اکشن، اگر URLای در گزینه‌ی [`navigate`](#navigate) تعیین شده باشد، به آن URL هدایت می‌کند. در غیر این صورت، رویداد [`notificationclick`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/notificationclick_event) روی سرویس‌کارگر صادر می‌شود؛ این رویداد شامل اکشن انتخاب‌شده (و نمونه‌ی `Notification` مرتبط) است تا سرویس‌کارگر بتواند بدون اینکه کاربر به صفحه‌ی شما برود، آن را مدیریت کند.

> [!NOTE]
> مرورگرها معمولاً حداکثر تعداد اکشن‌هایی را که برای یک اعلان خاص نمایش می‌دهند محدود می‌کنند. برای تعیین این حد، به ویژگی ایستای {{domxref("Notification.maxActions_static", "Notification.maxActions")}} مراجعه کنید.

## مثال‌ها

### استفاده‌ی پایه

کد زیر نشان می‌دهد که چگونه یک سرویس‌کارگر می‌تواند به رویداد `notificationclick` گوش دهد و از آن برای دریافت اکشن کلیک‌شده و همچنین آرایه‌ای از همه‌ی اکشن‌ها استفاده کند.

```js
// sw.js
self.addEventListener("notificationclick", (event) => {
  const clickedAction = event.action; // e.g. "reply" or "" if body was clicked

  // Read all defined actions
  const notification = event.notification; // the Notification object
  console.log(notification.actions); // full array of action objects

  notification.close();
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)
- {{domxref("Notification.maxActions_static", "Notification.maxActions")}}