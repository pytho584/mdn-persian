---
title: PushEvent
slug: Web/API/PushEvent
page-type: web-api-interface
browser-compat: api.PushEvent
---

{{APIRef("Push API")}}{{SecureContext_Header}}{{AvailableInWorkers("service")}}

رابط **`PushEvent`** در [Push API](/en-US/docs/Web/API/Push_API) نمایانگر یک پیام پوش (Push) دریافت‌شده است. این رویداد به [حوزهٔ سراسری](/en-US/docs/Web/API/ServiceWorkerGlobalScope) یک {{domxref("ServiceWorker")}} ارسال می‌شود و شامل اطلاعاتی است که از سرور اپلیکیشن به یک {{domxref("PushSubscription")}} ارسال شده است.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PushEvent.PushEvent", "PushEvent()")}}
  - : یک شیء `PushEvent` جدید می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("ExtendableEvent")}} به ارث می‌برد. ویژگی‌های اضافی:_

- {{domxref("PushEvent.data")}} {{ReadOnlyInline}}
  - : ارجاعی به یک شیء {{domxref("PushMessageData")}} برمی‌گرداند که شامل داده‌های ارسال‌شده به {{domxref("PushSubscription")}} است.

## متدهای نمونه

_متدها را از والد خود، {{domxref("ExtendableEvent")}} به ارث می‌برد._

## مثال‌ها

مثال زیر داده‌ها را از یک `PushEvent` می‌گیرد و آن‌ها را روی همهٔ کلاینت‌های آن سرویس‌ورکر نمایش می‌دهد.

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

  const notification = new self.Notification(title, {
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

## همچنین ببینید

- [Push API](/en-US/docs/Web/API/Push_API)
- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)