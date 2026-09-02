---
title: "IntersectionObserver: takeRecords() method"
---

---
title: "IntersectionObserver: takeRecords() method"
short-title: takeRecords()
slug: Web/API/IntersectionObserver/takeRecords
page-type: web-api-instance-method
browser-compat: api.IntersectionObserver.takeRecords
---

{{APIRef("Intersection Observer API")}}

متد **`takeRecords()`** از رابط {{domxref("IntersectionObserver")}} آرایه‌ای از اشیاء {{domxref("IntersectionObserverEntry")}} برمی‌گرداند؛ یکی برای هر عنصر هدف که از آخرین باری که تقاطع‌ها بررسی شده‌اند، تغییر تقاطع داشته است؛ خواه این بررسی به‌صورت صریح با فراخوانی این متد انجام شده باشد، خواه به‌صورت ضمنی با فراخوانی خودکار callback ناظر.

> [!NOTE]
> اگر از تابع callback برای نظارت بر این تغییرات استفاده می‌کنید، نیازی به فراخوانی این متد ندارید.
> فراخوانی این متد فهرست تقاطع‌های در انتظار را پاک می‌کند، بنابراین تابع callback اجرا نخواهد شد.

## سینتکس

```js-nolint
takeRecords()
```

### پارامترها

هیچ.

### مقدار بازگشتی

آرایه‌ای از اشیاء {{domxref("IntersectionObserverEntry")}}، یکی برای هر عنصر هدف که تقاطع آن با ریشه از آخرین بار بررسی تقاطع‌ها تغییر کرده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API)