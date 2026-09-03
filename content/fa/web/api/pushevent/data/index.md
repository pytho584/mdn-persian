---
title: "PushEvent: data property"
short-title: data
slug: Web/API/PushEvent/data
page-type: web-api-instance-property
browser-compat: api.PushEvent.data
---

{{APIRef("Push API")}}{{SecureContext_Header}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنیِ `data` در رابط **`PushEvent`**، ارجاعی به یک شیء {{domxref("PushMessageData")}} برمی‌گرداند که داده‌های ارسال‌شده به {{domxref("PushSubscription")}} را در بر دارد.

## مقدار

یک شیء {{domxref("PushMessageData")}} یا اگر هنگام نمونه‌سازی رویداد، عضوی به نام `data` ارسال نشده باشد، `null`.

## مثال‌ها

مثال زیر داده‌ها را از یک PushEvent می‌گیرد و آن‌ها را در همهٔ کلاینت‌های service worker نمایش می‌دهد.

```js
self.addEventListener("push", (event) => {
  if (!(self.Notification && self.Notification.permission === "granted")) {
    return;
  }

  const data = event.data?.json() ?? {};
  const title = data.title || "Something Has Happened";
  const message =
    data.message || "Here's something you might want to check out.";
  const icon = "images/new-notification.png";

  const notification = new Notification(title, {
    body: message,
    tag: "simple-push-demo-notification",
    icon,
  });

  notification.addEventListener("click", () => {
    clients.openWindow(
      "https://example.blog.com/2015/03/04/something-new.html",
    );
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}