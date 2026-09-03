---
title: "PeriodicSyncEvent: PeriodicSyncEvent() constructor"
short-title: PeriodicSyncEvent()
slug: Web/API/PeriodicSyncEvent/PeriodicSyncEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.PeriodicSyncEvent.PeriodicSyncEvent
---

{{APIRef("Periodic Background Sync")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

سازندهٔ **`PeriodicSyncEvent()`** یک شیء جدید {{domxref("PeriodicSyncEvent")}} می‌سازد. معمولاً از این سازنده استفاده نمی‌شود. مرورگر این اشیاء را به‌تنهایی می‌سازد و آن‌ها را در اختیار فراخوانِ (callback) رویداد {{domxref('ServiceWorkerGlobalScope.periodicsync_event', 'onperiodicsync')}} قرار می‌دهد.

## سینتکس

```js-nolint
new PeriodicSyncEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است حاوی نام رویداد. این مقدار به بزرگی/کوچکی حروف حساس است و مرورگرها آن را روی `periodicsync` تنظیم می‌کنند.
- `options`
  - : شیءای که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:

    - `tag`
      - : برچسب مرتبط با رویداد همگام‌سازی.

### مقدار بازگشتی

یک شیء جدید {{domxref("PeriodicSyncEvent")}} که با استفاده از ورودی‌های داده‌شده پیکربندی شده است.

## مثال‌ها

این مثال یک {{domxref('PeriodicSyncEvent')}} جدید با برچسب مرتبط می‌سازد.

```js
const psEvent = new ExtendableEvent("periodicsync", { tag: "unique-tag" });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تجربه‌های آفلاین غنی‌تر با Periodic Background Sync API](https://developer.chrome.com/docs/capabilities/periodic-background-sync)