---
title: "PressureObserver: knownSources static property"
short-title: knownSources
slug: Web/API/PressureObserver/knownSources_static
page-type: web-api-static-property
status:
  - experimental
browser-compat: api.PressureObserver.knownSources_static
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

ویژگی استاتیکِ فقط‌خواندنی **`knownSources`** در رابط {{domxref("PressureObserver")}} آرایه‌ای از مقادیر {{domxref("PressureRecord.source","source")}} را که عامل کاربر (user agent) از آن‌ها پشتیبانی می‌کند، به‌ترتیب حروف الفبا برمی‌گرداند.

> [!NOTE]
> فهرست منابع پشتیبانی‌شده بسته به مرورگر، سیستم‌عامل و سخت‌افزار متفاوت است و همچنان در حال تکامل است. این ویژگی صرفاً اشاره‌ای دربارهٔ نوع منابعی است که عامل کاربر پشتیبانی می‌کند. برای اینکه ببینید آیا مشاهدهٔ فشار ممکن است، متد {{domxref("PressureObserver.observe()", "observe()")}} را فراخوانی کنید و وجود خطای `NotSupportedError` را بررسی کنید.

## مقدار

آرایه‌ای از مقادیر {{domxref("PressureRecord.source")}}.

## مثال‌ها

### استفاده از کنسول برای مشاهدهٔ منابع شناخته‌شده

برای اینکه بفهمید مرورگر کدام مقادیر {{domxref("PressureRecord.source","source")}} را می‌شناسد، عبارت <kbd>PressureObserver.knownSources</kbd> را در کنسول وارد کنید. این کار آرایه‌ای از منابع شناخته‌شده را برمی‌گرداند.

```js
PressureObserver.knownSources;
// returns ["cpu"] in Chrome 125
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}