---
title: EventCounts
slug: Web/API/EventCounts
page-type: web-api-interface
browser-compat: api.EventCounts
---

{{APIRef("Performance API")}}

رابط **`EventCounts`** از [Performance API](/en-US/docs/Web/API/Performance_API) تعداد رویدادهایی را فراهم می‌کند که برای هر نوع رویداد ارسال شده‌اند.

یک نمونه‌ی `EventCounts` یک [شیءِ شبیه به `Map`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis) فقط‌خواندنی است که در آن هر کلید، نام رشته‌ای (string) یک نوع رویداد است و مقدار متناظر با آن، یک عدد صحیح است که تعداد رویدادهای ارسال‌شده برای آن نوع رویداد را نشان می‌دهد.

## سازنده

این رابط سازنده‌ای ندارد. معمولاً نمونه‌ای از این شیء را با استفاده از خاصیت {{domxref("performance.eventCounts")}} دریافت می‌کنید.

## ویژگی‌های نمونه

- `size`
  - برای جزئیات، {{jsxref("Map.prototype.size")}} را ببینید.

## متدهای نمونه

- `entries()`
  - برای جزئیات، {{jsxref("Map.prototype.entries()")}} را ببینید.
- `forEach()`
  - برای جزئیات، {{jsxref("Map.prototype.forEach()")}} را ببینید.
- `get()`
  - برای جزئیات، {{jsxref("Map.prototype.get()")}} را ببینید.
- `has()`
  - برای جزئیات، {{jsxref("Map.prototype.has()")}} را ببینید.
- `keys()`
  - برای جزئیات، {{jsxref("Map.prototype.keys()")}} را ببینید.
- `values()`
  - برای جزئیات، {{jsxref("Map.prototype.values()")}} را ببینید.

## مثال‌ها

### کار با مپ‌های EventCount

در زیر چند مثال برای دریافت اطلاعات از یک مپ `EventCounts` آورده شده است. توجه داشته باشید که این مپ فقط‌خواندنی است و متدهای `clear()`، `delete()` و `set()` در دسترس نیستند.

```js
for (entry of performance.eventCounts.entries()) {
  const type = entry[0];
  const count = entry[1];
}

const clickCount = performance.eventCounts.get("click");

const isExposed = performance.eventCounts.has("mousemove");
const exposedEventsCount = performance.eventCounts.size;
const exposedEventsList = [...performance.eventCounts.keys()];
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("performance.eventCounts")}}
- {{domxref("PerformanceEventTiming")}}
- {{jsxref("Map")}}