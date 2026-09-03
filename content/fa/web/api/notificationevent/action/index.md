---
title: "NotificationEvent: action property"
short-title: action
slug: Web/API/NotificationEvent/action
page-type: web-api-instance-property
browser-compat: api.NotificationEvent.action
---

{{APIRef("Web Notifications")}}{{AvailableInWorkers("service")}}

خاصیت فقط‌خواندنی **`action`** از رابط {{domxref("NotificationEvent")}}، شناسه رشته‌ای دکمه اعلانی را که کاربر کلیک کرده است، برمی‌گرداند. این مقدار در صورتی که کاربر روی جایی غیر از دکمه اقدام (action button) کلیک کرده باشد، یا اعلان (notification) دکمه‌ای نداشته باشد، یک رشته خالی برمی‌گرداند. شناسه دکمه اقدام در زمان ایجاد اعلان از طریق ویژگی آرایه‌ای `actions` تنظیم می‌شود و تا زمانی که اعلان جایگزین نشود، قابل تغییر نیست.

## مقدار

یک رشته.

## مثال‌ها

```js
self.registration.showNotification("New articles available", {
  actions: [{ action: "get", title: "Get now." }],
});

self.addEventListener("notificationclick", (event) => {
  event.notification.close();
  if (event.action === "get") {
    synchronizeReader();
  } else {
    clients.openWindow("/reader");
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}