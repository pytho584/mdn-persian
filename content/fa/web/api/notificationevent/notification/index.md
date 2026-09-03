---
title: "NotificationEvent: notification property"
---

---
title: "NotificationEvent: notification property"
short-title: notification
slug: Web/API/NotificationEvent/notification
page-type: web-api-instance-property
browser-compat: api.NotificationEvent.notification
---

{{APIRef("Web Notifications")}}{{AvailableInWorkers("service")}}

خاصیت فقط‌خواندنی **`notification`** از رابط {{domxref("NotificationEvent")}}، نمونه‌ای از {{domxref("Notification")}} را برمی‌گرداند که برای فعال‌کردن رویداد، روی آن کلیک شده است. {{domxref("Notification")}} دسترسی فقط‌خواندنی به ویژگی‌های زیادی فراهم می‌کند که در زمان نمونه‌سازی Notification تنظیم شده‌اند، مانند ویژگی‌های `tag` و `data` که به شما امکان می‌دهند اطلاعاتی را برای استفادهٔ تأخیری در رویداد `notificationclick` ذخیره کنید.

## مقدار

یک شیء {{domxref("Notification")}}.

## نمونه‌ها

```js
self.addEventListener("notificationclick", (event) => {
  console.log("On notification click");

  // Data can be attached to the notification so that you
  // can process it in the notificationclick handler.
  console.log(`Notification Tag: ${event.notification.tag}`);
  console.log(`Notification Data: ${event.notification.data}`);
  event.notification.close();

  // This looks to see if the current is already open and
  // focuses if it is
  event.waitUntil(
    clients
      .matchAll({
        type: "window",
      })
      .then((clientList) => {
        for (const client of clientList) {
          if (client.url === "/" && "focus" in client) return client.focus();
        }
        if (clients.openWindow) return clients.openWindow("/");
      }),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}