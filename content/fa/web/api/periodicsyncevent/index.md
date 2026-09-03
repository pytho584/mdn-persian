---
title: PeriodicSyncEvent
slug: Web/API/PeriodicSyncEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PeriodicSyncEvent
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

رابط **`PeriodicSyncEvent`** از {{domxref('Web Periodic Background Synchronization API', '', '', 'nocode')}} راهی برای اجرای وظایف در سرویس‌ورکر هنگام برقراری اتصال شبکه فراهم می‌کند.

یک نمونه از این رویداد به هندلر {{domxref('ServiceWorkerGlobalScope.periodicsync_event', 'periodicsync')}} ارسال می‌شود. این اتفاق به‌صورت دوره‌ای، با بازه‌ای بزرگ‌تر یا مساوی بازهٔ تنظیم‌شده در متد {{domxref('PeriodicSyncManager.register()')}} رخ می‌دهد. عوامل دیگری که به پیاده‌سازی مرورگر بستگی دارند، مانند میزان تعامل کاربر با سایت، بازهٔ واقعی را تعیین می‌کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PeriodicSyncEvent.PeriodicSyncEvent", "PeriodicSyncEvent()")}} {{Experimental_Inline}}
  - : یک شیء `PeriodicSyncEvent` جدید می‌سازد. این سازنده معمولاً به‌طور مستقیم استفاده نمی‌شود؛ مرورگر خودش این اشیاء را می‌سازد و آن‌ها را در اختیار فراخوان {{domxref('ServiceWorkerGlobalScope.periodicsync_event', 'onperiodicsync')}} قرار می‌دهد.

## ویژگی‌های نمونه

_ویژگی‌های زیر را از والد خود، {{domxref('ExtendableEvent')}} به ارث می‌برد._

- {{domxref('PeriodicSyncEvent.tag')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شناسهٔ تعریف‌شده توسط توسعه‌دهنده را برای این `PeriodicSyncEvent` بازمی‌گرداند. وب‌اپلیکیشن می‌تواند از چندین برچسب برای اجرای وظایف دوره‌ای مختلف با بسامدهای مختلف استفاده کند.

## متدهای نمونه

_متدهای زیر را از والد خود، {{domxref('ExtendableEvent')}} به ارث می‌برد._

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه می‌توان به یک رویداد همگام‌سازی دوره‌ای در سرویس‌ورکر پاسخ داد.

```js
self.addEventListener("periodicsync", (event) => {
  if (event.tag === "get-latest-news") {
    event.waitUntil(fetchAndCacheLatestNews());
  }
});
```

تابع `fetchAndCacheLatestNews` تابعی است که توسعه‌دهنده آن را تعریف می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تجربه‌های آفلاین غنی‌تر با Periodic Background Sync API](https://developer.chrome.com/docs/capabilities/periodic-background-sync)