---
title: "Profiler: Profiler() constructor"
short-title: Profiler()
slug: Web/API/Profiler/Profiler
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.Profiler.Profiler
---

{{APIRef("JS Self-Profiling API")}}{{SeeCompatTable}}

سازندهٔ **`Profiler()`** یک شیء جدید {{domxref("Profiler")}} می‌سازد.

پس از ساخته‌شدن، پروفایلرِ جدید شروع به جمع‌آوری نمونه‌ها می‌کند.

## Syntax

```js-nolint
new Profiler(options)
```

### Parameters

- `options`
  - : تنظیمات این پروفایلر. این یک شیء است که شامل ویژگی‌های زیر می‌باشد:
    - `maxBufferSize`
      - : عددی که حداکثر تعداد نمونه‌هایی را مشخص می‌کند که قرار است گرفته شوند. وقتی تعداد نمونه‌ها به این عدد برسد، مرورگر رویداد {{domxref("Profiler.samplebufferfull_event", "samplebufferfull")}} را برای پروفایلر صادر می‌کند و دیگر هیچ نمونه‌ای ثبت نخواهد شد.
    - `sampleInterval`
      - : فاصلهٔ زمانی بین هر دو نمونه‌برداری، بر حسب میلی‌ثانیه.

### Exceptions

- `RangeError` {{domxref("DOMException")}}
  - : اگر گزینهٔ `sampleInterval` کمتر از صفر باشد، این خطا پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر سند با [document policy](https://wicg.github.io/document-policy/) که شامل نقطهٔ پیکربندی `"js-profiling"` است ارائه نشده باشد، این خطا پرتاب می‌شود.

## Examples

این مثال یک پروفایلر می‌سازد که حداکثر ۱۰۰۰ نمونه برمی‌دارد و هر ۱۰ میلی‌ثانیه یک بار نمونه‌برداری می‌کند.

```js
const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 1000 });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}