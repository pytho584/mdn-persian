---
title: "PressureObserver: unobserve() method"
short-title: unobserve()
slug: Web/API/PressureObserver/unobserve
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PressureObserver.unobserve
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

متد **`unobserve()`** از رابط {{domxref('PressureObserver')}}، تماس callback ناظر فشار را از دریافت رکوردهای فشار از منبع مشخص‌شده متوقف می‌کند.

## نحو (Syntax)

```js-nolint
unobserve(source)
```

### پارامترها

- `source`
  - : یک رشته که مشخص می‌کند کدام {{domxref("PressureRecord.source", "source")}} را از مشاهده خارج کنیم.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### توقف مشاهده یک منبع خاص

مثال زیر نحوه توقف مشاهده منبع `"gpu"` را پس از آنکه ناظر قبلاً هر دو منبع `"cpu"` و `"gpu"` را مشاهده می‌کرد، نشان می‌دهد.

```js
const observer = new PressureObserver(callback);

observer.observe("cpu");
observer.observe("gpu");

// Callback now gets called whenever the pressure state changes for 'cpu' or 'gpu'.

observer.unobserve("gpu");

// Callback now only gets called whenever the pressure state changes for 'cpu'.
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}