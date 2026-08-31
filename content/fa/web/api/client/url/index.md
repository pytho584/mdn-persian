---
title: "Client: url property"
short-title: url
slug: Web/API/Client/url
page-type: web-api-instance-property
browser-compat: api.Client.url
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`url`** از رابط {{domxref("Client")}}، نشانی اینترنتی (URL) کلاینتِ فعلیِ service worker را بازمی‌گرداند.

توجه داشته باشید که ویژگی `url` به‌روزرسانی نمی‌شود مگر اینکه یک صفحهٔ جدید واقعاً بارگذاری شود. این بدان معناست که اگر کاربر در همان صفحه با استفاده از قطعهٔ URL پیمایش کند، یا اگر یک برنامهٔ تک‌صفحه‌ای ({{glossary("SPA", "single-page app (SPA)")}}) یک رویداد پیمایش را رهگیری کند (مثلاً با استفاده از [Navigation API](/en-US/docs/Web/API/Navigation_API)) و محتوای صفحه را با کد سمت کلاینت به‌روزرسانی کند، این ویژگی تغییر نخواهد کرد.

## مقدار

یک رشته (string).

## مثال‌ها

```js
self.addEventListener("notificationclick", (event) => {
  console.log("On notification click: ", event.notification.tag);
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
          if (client.url === "/" && "focus" in client) {
            return client.focus();
          }
        }
        if (clients.openWindow) {
          return clients.openWindow("/");
        }
      }),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}