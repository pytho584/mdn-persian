---
title: "NotificationEvent"
---

---
title: NotificationEvent
slug: Web/API/NotificationEvent
page-type: web-api-interface
browser-compat: api.NotificationEvent
---

{{APIRef("Web Notifications")}}{{AvailableInWorkers("service")}}

رابط **`NotificationEvent`** در {{domxref("Notifications API", "", "", "nocode")}} نمایانگر یک رویداد اعلان است که روی {{domxref("ServiceWorkerGlobalScope")}} متعلق به یک {{domxref("ServiceWorker")}} ارسال می‌شود.

این رابط از رابط {{domxref("ExtendableEvent")}} ارث می‌برد.

> [!NOTE]
> فقط رویدادهای اعلان ماندگار، که روی شیء {{domxref("ServiceWorkerGlobalScope")}} رخ می‌دهند، رابط `NotificationEvent` را پیاده‌سازی می‌کنند. رویدادهای اعلان غیرماندگار، که روی شیء {{domxref("Notification")}} رخ می‌دهند، رابط `Event` را پیاده‌سازی می‌کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("NotificationEvent.NotificationEvent","NotificationEvent()")}}
  - : یک شیء جدید از نوع `NotificationEvent` می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌ها را از رابط والد خود، یعنی {{domxref("ExtendableEvent")}}، به ارث می‌برد._

- {{domxref("NotificationEvent.notification")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("Notification")}} برمی‌گرداند که نمایانگر اعلانی است که برای فعال‌سازی رویداد روی آن کلیک شده است.
- {{domxref("NotificationEvent.action")}} {{ReadOnlyInline}}
  - : شناسهٔ رشته‌ای دکمهٔ اعلان را برمی‌گرداند که کاربر روی آن کلیک کرده است. اگر کاربر روی نقطه‌ای از اعلان غیر از یک دکمهٔ عملیات کلیک کند، یا اگر اعلان دارای دکمه نباشد، این مقدار یک رشتهٔ خالی برمی‌گرداند.

## متدهای نمونه

_همچنین متدها را از رابط والد خود، یعنی {{domxref("ExtendableEvent")}}، به ارث می‌برد._

## مثال

```js
self.addEventListener("notificationclick", (event) => {
  console.log(`On notification click: ${event.notification.tag}`);
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

> [!NOTE]
> این رابط در [Notifications API](/en-US/docs/Web/API/Notifications_API) مشخص شده است، اما از طریق {{domxref("ServiceWorkerGlobalScope")}} در دسترس است.

## سازگاری مرورگر

{{Compat}}