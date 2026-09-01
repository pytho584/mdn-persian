---
title: "ExtendableCookieChangeEvent"
---

---
title: ExtendableCookieChangeEvent
slug: Web/API/ExtendableCookieChangeEvent
page-type: web-api-interface
browser-compat: api.ExtendableCookieChangeEvent
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("service")}}

رابط **`ExtendableCookieChangeEvent`** از {{domxref("Cookie Store API", "", "", "nocode")}} نوع رویدادی است که به رویداد {{domxref("ServiceWorkerGlobalScope/cookiechange_event", "cookiechange")}} ارسال می‌شود. این رویداد در {{domxref("ServiceWorkerGlobalScope")}} هنگام رخ دادن هر تغییر کوکی که با فهرست اشتراک تغییرات کوکیِ service worker (سرویس‌کارگر) مطابقت داشته باشد، ایجاد می‌شود. یک رویداد تغییر کوکی شامل یک کوکی و یک نوع (یا "changed" یا "deleted") است.

تغییرات کوکی که موجب ارسال `ExtendableCookieChangeEvent` می‌شوند عبارتند از:

- یک کوکی تازه ایجاد شود و بلافاصله حذف نشود، یا اگر یک کوکی جایگزین شود. در این حالت `type` برابر با "changed" است.
- یک کوکی تازه ایجاد شود و بلافاصله حذف شود. در این حالت `type` برابر با "deleted" است.
- یک کوکی حذف شود. در این حالت `type` برابر با "deleted" است.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ExtendableCookieChangeEvent.ExtendableCookieChangeEvent", "ExtendableCookieChangeEvent()")}}
  - : یک `ExtendableCookieChangeEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("ExtendableEvent")}} به ارث می‌برد._

- {{domxref("ExtendableCookieChangeEvent.changed")}} {{ReadOnlyInline}}
  - : یک آرایه شامل کوکی‌های تغییر یافته را بازمی‌گرداند.
- {{domxref("ExtendableCookieChangeEvent.deleted")}} {{ReadOnlyInline}}
  - : یک آرایه شامل کوکی‌های حذف‌شده را بازمی‌گرداند.

## متدهای نمونه

_این رابط همچنین متدهایی را از {{domxref("ExtendableEvent")}} به ارث می‌برد._

## مثال‌ها

در مثال زیر، از {{domxref("CookieStoreManager.getSubscriptions()")}} برای دریافت فهرستی از اشتراک‌های موجود استفاده می‌کنیم. (در سرویس‌کارگرها، برای گوش دادن به رویدادها، اشتراک لازم است.) با استفاده از {{domxref("CookieStoreManager.unsubscribe()")}} اشتراک‌های موجود را لغو می‌کنیم و سپس با استفاده از {{domxref("CookieStoreManager.subscribe()")}} در کوکی با نام 'COOKIE_NAME' اشتراک می‌گیریم. اگر آن کوکی تغییر کند، شنوندهٔ رویداد، رویداد را در کنسول ثبت می‌کند. این یک شیء `ExtendableCookieChangeEvent` خواهد بود که ویژگی {{domxref("ExtendableCookieChangeEvent.changed","changed")}} یا {{domxref("ExtendableCookieChangeEvent.deleted","deleted")}} آن شامل کوکی تغییر یافته است.

```js
self.addEventListener("activate", (event) => {
  event.waitUntil(async () => {
    const subscriptions = await self.registration.cookies.getSubscriptions();

    await self.registration.cookies.unsubscribe(subscriptions);

    await self.registration.cookies.subscribe([
      {
        name: "COOKIE_NAME",
      },
    ]);
  });
});

self.addEventListener("cookiechange", (event) => {
  console.log(event);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}