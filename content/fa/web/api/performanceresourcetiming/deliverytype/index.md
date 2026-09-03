---
title: "PerformanceResourceTiming: deliveryType property"
short-title: deliveryType
slug: Web/API/PerformanceResourceTiming/deliveryType
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.deliveryType
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`deliveryType`** یک رشته است که نحوه تحویل منبع را مشخص می‌کند — برای مثال از حافظه نهان (cache) یا از یک پیش‌واکشی ناوبری (navigational prefetch).

## مقدار

یک رشته که می‌تواند یکی از مقادیر زیر باشد:

- `"cache"`
  - : منبع از حافظه نهان (cache) بازیابی شده است.
- `"navigational-prefetch"` {{experimental_inline}} {{non-standard_inline}}
  - : منبع از یک پاسخ پیش‌واکشی شده که در حافظه نهان درون‌حافظه‌ای (in-memory cache) از طریق [API قوانین حدس (Speculation Rules API)](/en-US/docs/Web/API/Speculation_Rules_API) ذخیره شده است، بازیابی شده است.
- `""` (رشته خالی)
  - : در صورتی که هیچ‌یک از انواع تحویل فوق اعمال نشوند، بازگردانده می‌شود.

## مثال‌ها

### فیلتر کردن منابع

از ویژگی `deliveryType` می‌توان برای دریافت فقط ورودی‌های زمان‌بندی منبع خاص استفاده کرد؛ برای مثال فقط آن‌هایی که در حافظه نهان ذخیره شده‌اند.

مثال زیر از یک {{domxref("PerformanceObserver")}} استفاده می‌کند تا ورودی‌های عملکرد `resource` جدید را هنگام ثبت در خط زمانی عملکرد مرورگر اعلام کند. گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد ناظر استفاده می‌شود.

```js
const observer = new PerformanceObserver((list) => {
  const cachedResources = list
    .getEntries()
    .filter((entry) => entry.deliveryType === "cache");
  console.log(cachedResources);
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکرد `resource` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی متد نشان می‌دهد.

```js
const scripts = performance
  .getEntriesByType("resource")
  .filter((entry) => entry.deliveryType === "cache");
console.log(scripts);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}