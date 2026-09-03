---
title: "Performance: resourcetimingbufferfull event"
short-title: resourcetimingbufferfull
slug: Web/API/Performance/resourcetimingbufferfull_event
page-type: web-api-event
browser-compat: api.Performance.resourcetimingbufferfull_event
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

هنگامی که [بافر زمان‌بندی منابع](/en-US/docs/Web/API/Performance/setResourceTimingBufferSize) مرورگر پر می‌شود، رویداد `resourcetimingbufferfull` فعال می‌شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگی کنترل‌کننده رویداد:

```js-nolint
addEventListener("resourcetimingbufferfull", (event) => { })

onresourcetimingbufferfull = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### افزایش اندازه بافر هنگام پر شدن آن

در مثال زیر، به رویداد `resourcetimingbufferfull` گوش داده می‌شود و با استفاده از روش {{domxref("Performance.setResourceTimingBufferSize", "setResourceTimingBufferSize()")}} اندازه بافر افزایش می‌یابد.

```js
function increaseFilledBufferSize(event) {
  console.log(
    "WARNING: Resource Timing Buffer is FULL! Increasing buffer size to 500.",
  );
  performance.setResourceTimingBufferSize(500);
}

performance.addEventListener(
  "resourcetimingbufferfull",
  increaseFilledBufferSize,
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Performance.clearResourceTimings()")}}
- {{domxref("Performance.setResourceTimingBufferSize()")}}