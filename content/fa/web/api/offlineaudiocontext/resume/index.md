---
title: "OfflineAudioContext: resume() method"
short-title: resume()
slug: Web/API/OfflineAudioContext/resume
page-type: web-api-instance-method
browser-compat: api.OfflineAudioContext.resume
---

{{ APIRef("Web Audio API") }}

متد **`resume()`** در رابط {{domxref("OfflineAudioContext")}}، پیشروی زمان را در زمینه‌ی صوتی‌ای که معلق شده است، از سر می‌گیرد. این پرامیس بلافاصله حل می‌شود، زیرا `OfflineAudioContext` به سخت‌افزار صوتی نیازی ندارد.

## نحو (Syntax)

```js-nolint
resume()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{jsxref('undefined')}} حل می‌شود.

### استثناها

در صورت بروز استثنا، پرامیس رد می‌شود.

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر زمینه در حال حاضر معلق نباشد یا رندرینگ شروع نشده باشد، بازگردانده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}