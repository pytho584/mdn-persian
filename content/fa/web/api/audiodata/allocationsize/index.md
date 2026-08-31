---
title: "AudioData: allocationSize() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioData/allocationSize"
translated_by: "n8n + AI"
---

---
title: "AudioData: allocationSize() method"
short-title: allocationSize()
slug: Web/API/AudioData/allocationSize
page-type: web-api-instance-method
browser-compat: api.AudioData.allocationSize
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`allocationSize()`** از رابط {{domxref("AudioData")}} اندازه بر حسب بایت مورد نیاز برای نگه‌داری نمونه فعلی را بر اساس گزینه‌های ارسال‌شده به متد برمی‌گرداند.

## نحو

```js-nolint
allocationSize(options)
```

### پارامترها

- `options`
  - : یک شیء شامل موارد زیر:
    - `planeIndex`
      - : شاخص صفحه‌ای که اندازه آن را می‌خواهید برگردانید.
    - `frameOffset` {{optional_inline}}
      - : یک عدد صحیح که یک افست در داده‌های صفحه را مشخص می‌کند و نشان می‌دهد از کدام صفحه شروع شود. پیش‌فرض `0` است.
    - `frameCount` {{optional_inline}}
      - : یک عدد صحیح که تعداد فریم‌هایی را که اندازه آن‌ها را می‌خواهید برگردانید مشخص می‌کند. اگر حذف شود، تمام فریم‌های صفحه استفاده می‌شوند، از فریم مشخص‌شده در `frameOffset` شروع می‌شود.

### مقدار بازگشتی

یک عدد صحیح شامل تعداد بایت‌های مورد نیاز برای نگه‌داری نمونه‌های توصیف‌شده توسط `options`.

## مثال‌ها

مثال زیر اندازه صفحه در شاخص `1` را دریافت می‌کند.

```js
let size = AudioData.allocationSize({ planeIndex: 1 });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}