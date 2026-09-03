---
title: "Profiler: stop() method"
short-title: stop()
slug: Web/API/Profiler/stop
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Profiler.stop
---

{{APIRef("JS Self-Profiling API")}}{{SeeCompatTable}}

متد **`stop()`** از رابط {{domxref("Profiler")}} پروفایلر را متوقف می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که با خود پروفایل (profile) resolve می‌شود.

## Syntax

```js-nolint
stop()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء حاوی داده‌های پروفایل resolve می‌شود. قالب و تفسیر این شیء در [آناتومی و قالب پروفایل](/en-US/docs/Web/API/JS_Self-Profiling_API/Profile_content_and_format) توضیح داده شده است.

## مثال‌ها

### ضبط یک پروفایل

کد زیر عملیات `doWork()` را پروفایل می‌کند و نتیجه را در خروجی (log) نمایش می‌دهد.

```js
const profiler = new Profiler({ sampleInterval: 10, maxBufferSize: 10000 });

doWork();

const profile = await profiler.stop();
console.log(JSON.stringify(profile));
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}